---
title: "Package installation from CD etc."
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by ducko on 2005-02-02
This is very basic stuff, very n00bish but anyway! I have only a modem connection in my home machine into which I've planned to install Ubuntu. Basic system is easily installed from CD but howabout extra software which is too huge to apt-get with modem? Is it possible in any reasonable way to install Ubuntu/deb-packages from local directory using original packages from Ubuntu/Debian with apt? Or is it more reasonable to do it from the sources? The idea would be of course to use apt for checking dependencies. And where to get single Ubuntu-packages to download to be burned in CD?

---

### Post by dikki on 2005-02-02
Well, the /etc/apt/sources.list contains the sources from where you can download the .deb packages. There are seven lines in it, beginning with "deb" . 

The cdrom - line refers to the Ubuntu cd-rom, you can install some packages from there. If you would like to install something what you have on the cdrom, you can do it easily with apt-get.

And the first hit in google, for "ubuntu +packages" is:

[http://higgs.djpig.de/ubuntu/www/](http://higgs.djpig.de/ubuntu/www/)

You can download these and other packages everywhere, with apt-get install <packagename> -d  (download-only). See "man apt-get" . And you can burn these packages to a cd, or copy them to a pendrive, and install at home when necessary.

---

### Post by ducko on 2005-02-03
Yeah! Thanks *dikki* for reply! This 'little' apt thingy got me confused, I've never used it before ... my earlier experiments were with Slackware. Reading man pages for apt-get and a few good hints from Debian heavy users got me back on the tracks ... hopefully: All the stuff you download or move/copy from some other media must be placed in the archive directory '/var/cache/apt/archives'. You just have to take care that all needed packages are copied to 'archive' directory. There are some switches in apt-get to show what you need (before downloading) ... can't remember exactly now ... it had something to do with urls?! But anyway: It can be solved! ;^) !

---

