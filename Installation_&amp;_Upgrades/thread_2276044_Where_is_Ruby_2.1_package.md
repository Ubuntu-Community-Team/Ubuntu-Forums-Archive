---
title: "Where is Ruby 2.1 package??"
date: 2015-04-30
forum: Installation &amp; Upgrades
---

### Post by kazakore on 2015-04-30
[SIZE=2][FONT=arial][COLOR=#000000]I am trying to install Ruby 2.1 so that I can compile Sonic-Pi and give it a go.

[/COLOR][[COLOR=#000000]https://github.com/samaaron/sonic-pi/blob/master/INSTALL.md#generic-linux[/COLOR]]("https://github.com/samaaron/sonic-pi/blob/master/INSTALL.md#generic-linux")[COLOR=#000000]

Running 
sudo apt-get install supercollider ruby2.1 libqscintilla2-dev  ruby-dev cmake pkg-config 

and I get
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ruby2.1
E: Couldn't find any package by regex 'ruby2.1'

This page seems to list ruby2.1 as a valid package but clicking on APT Install button and it doesn't find it.
[/COLOR][[COLOR=#000000]http://www.ubuntuupdates.org/package/core/vivid/main/base/ruby2.1[/COLOR]]("http://www.ubuntuupdates.org/package/core/vivid/main/base/ruby2.1")[COLOR=#000000]

Installing just ruby installs ruby1.9 so not the correct version!

How do I install Ruby 2.1 via Apt so I can keep it updated?


EDIT: Ok I believe it's called 2.0 in Trusty.

[/COLOR][COLOR=#000000][http://www.ubuntuupdates.org/pm/ruby2.1]("http://http://www.ubuntuupdates.org/pm/ruby2.1")

...

except.
[/COLOR][/FONT][/SIZE][COLOR=#000000]$ ruby2.0 -v
[SIZE=2][FONT=arial]ruby 2.0.0p384 (2014-01-12) [x86_64-linux-gnu]


Sorry there a trusty 2.1 listed as well but it doesn't work!!

[http://www.ubuntuupdates.org/package/brightbox_ruby_ng_experimental/trusty/main/base/ruby2.1](http://www.ubuntuupdates.org/package/brightbox_ruby_ng_experimental/trusty/main/base/ruby2.1)[/FONT][/SIZE][/COLOR]

---

### Post by TheFu on 2015-04-30
Not a package manager solution, but most rubyists use rbenv or rvm to run their ruby apps, all gems, and ruby completely self-contained. 
This is a best practice - not using the Ubuntu packaged version.  There are many reasons to do it this way - chiefly so that ruby-based tools like puppet don't run into conflicts when folks need non-standard versions.  Non-standard really is just a way of saying "not the version Canonical determined would work with all the different programs in other packages." It isn't derogatory.

---

### Post by kazakore on 2015-04-30
Just noticed I was being a little blind and it states it's it a third party repo, not one of the standard ones. Added Brightbox Ruby NG Experimental[1] and it's not installing as expected :)

[1]http://www.ubuntuupdates.org/ppa/brightbox_ruby_ng_experimental?dist=trusty

---

