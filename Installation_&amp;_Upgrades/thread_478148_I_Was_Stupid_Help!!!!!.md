---
title: "I Was Stupid Help!!!!!"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by pieterminate on 2007-06-19
Ok, this very noobish person me needs help.....i did the "official upgrading" thing ("update-manager -c -d") but something went wrong in the middle and then it said something about x11G6 or something and then told me to remove some file so it can get some symlink or something.  And then i just randomly/accidentally deleted the /usr/bin/dpkg file :( Now everything is screwed up with downloading/installing stuff.  Is there anything in can do to fix this?

---

### Post by zanglang on 2007-06-19
Ouch! Um... don't ever delete anything in /usr/bin yourself. Remember that. ;)

I'm assuming you installed Feisty, right? If not, post here first before attempting anything.

Here's what you can do. Download this file:
[http://mirrors.kernel.org/ubuntu/pool/main/d/dpkg/dpkg_1.13.24ubuntu6_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dpkg/dpkg_1.13.24ubuntu6_i386.deb)

The following is off the top of my head so post again if they don't work. Open the .deb with the Archive manager (Right click, open with, choose Archive manager), look for a file inside a usr/bin directory somewhere in it and extract that. Then just 'sudo cp' it to /usr/bin. That should fill in your missing 'dpkg' nicely.

---

### Post by pieterminate on 2007-06-19
Ok, i've fixed the dpkg problem (just copied it from my other ubuntu computer).  Except upgrading to feisty is still not working...  "update-manager -c -d" results in it asking you to do a "apt-get install -f" but the "apt-get install -f" fails when it tries to extract the X11 stuff.  something about the X11R6 folder...  Has anyone else gotten these sorts of problems?  My computer is an old thinkpad which a Dapper install currently and i'm trying to upgrade it.  I don't want to entirely reinstall stuff since I have a lot of stuff randomly disorganzed in there, and also have this windows dualboot going on, etc.   HELP! :) :(

---

### Post by adom 00001 on 2007-08-22
i have a similar problem, i managed to delete /dpkg/update/  and now i can not install and apps or updates neither can i uninstall anything.  i i tried following the 'sudo cp'  advice but did not get far, i don't know how to use the 'cp' command.

---

