
# Installation

Currently only ruby is supported. I know I said ruhoh is _language-agnostic_, which it is! There is nothing in ruhoh that depends on ruby. However, I can only concentrate on one implementation at the moment so I picked ruby.

## Ruby and Rubygems

If you are new to ruby or don't know if you have have a 1.9.2+ ruby interpreter installed on your computer, please consult this guide from my buddies at http://nanoc.ws/install/ then hopefully come back here!

**NOTE** ruby 1.8.7 is not supported.

# Create Site Folder

First we create a folder to hold your ruhoh-enabled site. We'll name it "ruhoh-site":

{{# folder_tree }}
  ruhoh-site
    ...
{{/ folder_tree }}


# Ruhoh Gem

Ruhoh is packaged as a ruby gem which depends on:

- [rack](http://rubygems.org/gems/rack) - for web-server integration
- [directory\_watcher](http://rubygems.org/gems/directory_watcher) - for watching files for updates in realtime.
- [mustache](http://rubygems.org/gems/mustache) - for templating.
- [redcarpet](http://rubygems.org/gems/redcarpet) - for Markdown parsing.
- [nokogiri](http://rubygems.org/gems/nokogiri) - for DOM traversal and RSS support.

# Bundler

We use the ruby gem [Bundler][] to manage ruhoh gem versions.

Do you have bundler?

    $ bundle -v

If it's not found, install it:

    $ gem install bundler


## Gemfile

We need to create a [Gemfile][] that tells bundler which gems to bundle:

{{# folder_tree }}
  ruhoh-site
    Gemfile
{{/ folder_tree }}

Place the following contents inside the Gemfile:

    source "https://rubygems.org"
    gem 'ruhoh', "~> 2"


## Bundle Install

Install the bundle by opening a terminal session, navigating to your "ruhoh-site" folder and executing:

    $ bundle install


# Rack


Ruhoh uses the [Rack][] interface to run a local web-server but it is now built-in so all you need to do is, from within the "ruhoh-site" directory, run:

    $ bundle exec ruhoh server 9292

This starts a web server that serves your site here: [http://localhost:9292](http://localhost:9292)

# Terminal


To access the bundled ruhoh version you'll need precede your commands with `bundle exec ruhoh`:

    $ bundle exec ruhoh help
    $ bundle exec ruhoh console

`ruhoh` is the command-line-interface or CLI that interfaces with the ruhoh gem.

## Run without Bundler

To omit calling `bundler` with every command download the gem into your global environment:

    $ gem install ruhoh

Now you can make calls without bundler:

    $ ruhoh help
    $ ruhoh console

Note this will set `ruhoh` to the latest version so you can no longer easily switch across ruhoh versions.



# Next Steps

You can now continue with the [Quickstart Tutorial](/docs/2/quickstart) but you already have the initialization files so skip that part.



[Gemfile]: http://bundler.io/v1.3/gemfile.html
[Bundler]: http://bundler.io/
[Rack]: http://rack.github.io/
