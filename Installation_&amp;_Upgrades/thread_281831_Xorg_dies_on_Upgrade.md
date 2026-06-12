---
title: "Xorg dies on Upgrade"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by ANTDx1 on 2006-10-21
Alright so yesterday I decided to upgrade from 6.06 to 6.10 RC.  The normal update manager was having trouble, so I went ahead, changed all my repositories, and upgraded using apt.  I noticed that it timed out on some repositories, but my repository list is kind of a mess anyway.  Everything worked cool, all my appications updated on the fly, which was pretty cool.  However, when I restarted the computer, I got an error that said "xorg could not be loaded"  It asked me if I wanted to see the error message output, so I said yes.  It gave me a blank text thing similar to the old Ubuntu install screens, that just had "<ok>" at the bottom, with no other text.  After pressing enter on that ok, it said that I should restart gdm when my xserver configuration is correct.  Does anyone have any idea how I can fid out what's wrong with my config file, and/or replace the file.
Note: I am using amd Athlon64 with 64-bit Ubuntu on an HP zv6000.  I am using default 6.06 resolution, which I believe is 1280 by 800 for this particular machine.  If anyone knows what's wrong AND has a suitable replacement configuration file, or a way that I could fix it, that would be really cool.  Thanks for your help.

---

### Post by taurus on 2006-10-21
Why don't you reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by ANTDx1 on 2006-10-22
taurus, 
I tried doing that just now, and it came up withan error: xserver-xorg not fully installed.  I tried to apt-get install that package, and it gave me a bunch of dependency errors.  Most of them were related to openoffice.org, though one had something to do with mplayer, and others were xserver-xorg-core, and x11, or something like that.  Most of these seem to be trivial dependency issues, and quite honestly, I'd rather break my mplayer to get the gui working. I tried looking through the apt-get man files for something that might allow me to ignore dependencies, but I didn't find anything.  Any advice from anyone is, again, much appreciated.

---

