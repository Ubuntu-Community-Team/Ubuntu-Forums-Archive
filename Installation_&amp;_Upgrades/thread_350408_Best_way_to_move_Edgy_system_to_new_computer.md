---
title: "Best way to move Edgy system to new computer?"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by tommyp on 2007-01-31
I currently have Edgy running on an old P3-600 system, and would like to move the drive to a new system that I am building (an AMD Athalon 64). It will be the only drive in the new system (for now!)

My current HD has 3 partitions, each with stuff on it, but I have enough space that I can copy my existing root partition to any of the others.   I would like to avoid having to re-configure a bunch of stuff (my Myth backend, shortcut keys, firefox prefs, etc.) if possible.  

What is the best way to do this? 

Thanks!

---

### Post by glabouni on 2007-01-31
if you got your /home on a separate partition this should not be a problem as most of user preferences are stored in user's home directory.

if your /home is not on its own partition, these guides might help:

[Move /home to it&#8217;s own partition]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")
[Create a separate /home partition in Ubuntu]("http://www.psychocats.net/ubuntu/separatehome")

some configuration are stored in other places, so you should check beforehands you have a backup of the config files you want to save.

on another hand I think it might be possible to simply move the drive into the new computer and reconfiguring ubuntu for the new system. not sure this is possible if you plan to switch to 64bit version of ubuntu though.

---

### Post by kebes on 2007-01-31
The easiest would be to simply put the old hard drive in the new computer, and boot it up. Linux is pretty good about detecting and dealing with hardware changes (even when the entire computer changes!). I've done this before and it worked. You may need to fix your xorg.conf.

In any case, it's certainly worth a try, because there's a good chance everything will be detected and work.

You may want to make a backup image of your root partition (you can use a linux program called "partimage" from a LiveCD, such as [System Rescue CD]("http://www.sysresccd.org/Main_Page")). That way you can restore your root partition if something goes wrong, or copy your root partition to a new hard drive or whatever.

---

### Post by tommyp on 2007-01-31
Thanks!  I think I'll try just sticking it in (after copying the /root and moving /home) and see what happens.  I should probably have an install CD ready just in case.

Are there any folders in /root that would have user defined information (rather than hardware specific info, base program info, etc.)? I ask so that I know where to look if a re-install is required and things do work the way they do now.

---

### Post by kebes on 2007-01-31
Yeah have a a LiveCD ready at hand, for sure.


All your user settings are stored in /home/ (mostly in hidden files and directories, which start with a period ".") Most program settings will be stored here (like firefox bookmarks, etc.).

Settings for other programs may be spread out in various places. For instance many servers you have running may store settings in "/etc/" and many user-installed programs will be in "/usr/". If you know what programs you're worried about, you can usually find the file or two that stores the settings.

---

