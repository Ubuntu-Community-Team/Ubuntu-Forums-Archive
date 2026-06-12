---
title: "Editing Grub 2 Menu Help"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by apple_head on 2010-02-27
Hey i'm new to the Grub2 boot loader and want to change the layout...

This is how it looks at the moment:

Ubuntu (kernel name after)
Ubuntu (kernel name) Recovery Mode
Memtest
Memtest (console)
Microsoft Windows XP Professional

I'm trying to change it to this:

Linux:
Ubuntu 9.10 Karmic
Ubuntu 9.10 Karmic (Recovery Mode)
Memtest:
Memtest
Memtest (console)
Windows:
Windows XP Professional

Basically I would like to have all the entries organised into groups and I want to get a Grub GFX menu ???

Can anyone please point me in the right direction as to how to do this? :)

Many Thanks :)

---

### Post by oldfred on 2010-02-27
this is one way:
total custom menu/config file - meierfra 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

You can go in and modify the scripting to give you what you want:
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Separate grub partitions:
Herman on separate grub partition: 
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub partition slakkie
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/) 

Or you can turn off most or all of the grub scripts and just add what you want into 40_custom.

---

