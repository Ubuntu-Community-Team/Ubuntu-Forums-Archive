---
title: "Ruby doesn't appear to install properly"
date: 2005-10-10
forum: Installation &amp; Upgrades
---

### Post by andrewballantine on 2005-10-10
Hi,
I did search this forum,but nothing seemed to match.

I have installed Ruby using Synaptic, but when I open a terminal window and type ruby -v all I get is 

bash: ruby: command not found

Once Ruby is installed I then need to get Rails working.

Any help greatly appreciated.

Andrew Ballantine.

---

### Post by finlay on 2005-10-10
Assuming you installed the ruby1.8 package, you could just enter "ruby1.8"  (in places where you'd just say "ruby").

It's not a bad idea to make a symlink to your "preferred" ruby:

   sudo ln -s /usr/bin/ruby1.8 /usr/bin/ruby

---

### Post by andrewballantine on 2005-10-11
Thank you finlay.
It's these simple things that trip up us Linux newbies.
What a pity the ruby1.8 installation did not insert the symlink.
I say this because ALL the documentation for ruby says type "ruby"
I'll try and post this somewhere on the ruby site in the hope that someone will pick it up and add it to the installation procedure. Or should that be Debian perhaps?

Kind regards,

---

### Post by satellite360 on 2005-11-04
Did you manage to get Rails running?  I have installed Ruby which is working fine and have installed Rails but have no idea about the WEBrick part of the installation.  What does this mean? ...
[INDENT]Run the WEBrick servlet from DEST_DIR: script/server[/INDENT]

Any help would be much appreciated.

---

### Post by infoburner on 2005-12-31
once you get ruby working, go to [http://rubyforge.org/projects/rubygems/](http://rubyforge.org/projects/rubygems/) to get rubygems. download that tarball and extract it. then change into the folder it creates and type 
```
sudo ruby setup.rb
```
then all you have to do is type
```
sudo gem install rails
```
and gem will get and install rails and its dependencies for you as a gem file just like apt-get gets packages.

---

