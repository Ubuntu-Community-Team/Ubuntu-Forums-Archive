---
title: "snes9x-gtk in 32-bit ubuntu needs libpng14.so.14"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by osirisgothra on 2013-04-28
if you have installed snes9x as instructed to do so in this thread:

     [http://ubuntuforums.org/showthread.php?t=1921700](http://ubuntuforums.org/showthread.php?t=1921700)

you will need to get libpng14, on a 64-bit system this is already documented by this thread:

     [http://ubuntuforums.org/showthread.php?t=1659898](http://ubuntuforums.org/showthread.php?t=1659898)

HOWEVER, theres a small change for those of us (like me) who are using 32-bit version
also, i verified this on 32-bit versions of ubuntu 12.04, 12.10 and 13.04 (pre-release updated as of april 27, 2013)

first you will need to use these commands instead (which are simmilar, just changes the filename and folder where you get that file)
the commands do the following: 
[B]1) installs alien, which allows you to install RPM packages in ubuntu (an "alien" package)
2) grabs the rpm package that you will be converting to .deb and installing
3) run alien which will convert the RPM to a DEB and automatically run dpkg to install it for you
[/B]4) *(deleted) make a link to the 64-bit library file (not needed with the 32-bit version)*

for me, i just copied the following block of text into a terminal and that was enough but you may rather type them:

> 

sudo apt-get install alien

wget [ftp://rpmfind.net/linux/opensuse/update/11.4/rpm/i586/libpng14-14-1.4.4-3.6.1.i586.rpm](ftp://rpmfind.net/linux/opensuse/update/11.4/rpm/i586/libpng14-14-1.4.4-3.6.1.i586.rpm) 

sudo alien -i libpng14-14-1.4.4-3.6.1.x86_64.rpm



that's it, run snes9x-gtk and all will be well.... :) have fun
dont forget to thank the original people that came up with this, because it wasn't me! (see the link at the top)

---

