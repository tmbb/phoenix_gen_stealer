# phoenix_gen_stealer.exs

(Not to be confused with a [Genestealer](http://wh40k.lexicanum.com/wiki/Genestealer))

This is a small script I've written to help write customized Phoenix generators.
When run inside a mix project (with `mix run phoenix_gen_stealer.exs`), it will do the following:

  1. git clone the phoenix repo
  2. replace some of the file names and file contents, so that the phoenix namespace doesn't appear anymore
  3. Populate your mix project with the the minimum amount of files needed to run the generators (i.e. the generators themselves plus the file `phoenix/naming.ex`).
  4. Clean the temporary git repository

Your mix project now contains all the phoenix generators, customized so that they live inside your namespace.

The script doesn't currently accept user input.
This means that in order to integrate it into your project, you must edit these lines:

```
PhoenixGenStealer.steal(".",
  # Required:
  lowercase: "project",
  # All optional:
  uppercase: "Project",
  short_lowercase: "proj",
  short_uppercase: "Proj")
```

Just replace the options by the name of your project.
The meaning of the options is the following:

1. `phoenix` will be replaced by `:lowercase`
2. `Phoenix` will be replaced by `:uppercase`
3. `phx` will be replaced by `:short_lowercase`
4. `Phx` will be replaced by `:short_uppercase`

Only the first of these options is required.

Keep in mind that the generators extracted by this script may stop working in future phoenix versions.
Currently the generators only need the `naming.ex` file, but this might change in the future.

# How to use this script

The goal of this script is to create a mix project containing a bunch of working generators, which you can customize to your liking.

Such project can be included as a dev dependency in your phoenix apps, which will make such generators available in your app.

# Installation

I have no intentions of packaging or distributing this script in any way.
Feel free to package and distribute it somewhere if you please (but please prefer an escript to a mix archive).

# Inspirations

The script was inspired by [this discussion](https://elixirforum.com/t/customizing-mix-phoenix-gen-tasks/1468) in the Elixir forum.

# Disclaimer

I haven't tested *all* of the generators created by this script.
The ones I've tested have turned out okay.

# Legal

You can use this code for whatever you want.
No need to credit me.