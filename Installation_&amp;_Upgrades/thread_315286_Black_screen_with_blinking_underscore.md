---
title: "Black screen with blinking underscore"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by solinent on 2006-12-08
Well I decided to install linux on top of windows, so first to try it out I went into the AMD64 version of ubuntu 6.10 and gave it a try, and decided it was worth it.  So I am ready to resize my partition, so I decide to do a backup.  I finish the backup, and then download the 32 bit version of ubuntu after hearing of many concerns with the 64bit version (and how windows xp x86 runs on AMD64).  I am doing this just for personal use.

Ok, well once the boot screen takes forever (longer than the 64 bit version) I am given this black screen with a blinking underscore at the top, and I am unable to enter in any text or basically do anything.  So now I'm back on windows asking you whether I can install 32 bit ubuntu on a AMD64 computer:

AMD64 4400+ 
Asus Geforce 6600 GT
Asus motherboard (not exactly sure the motherboard)
250GB hard disc - no partition created for linux, I was planning on using the installer to create this partition.

-Anything else you may need to help me please ask!

By the way I'm a complete Newb and I've never installed linux before.  I'm just learning some commands of the internet.

EDIT:

Sorry I just saw the thread below entitled "Black screen during install" which applies to me.  If my problem is different or not then the mods can decide whether to lock this or whatever.

---

### Post by K.Mandla on 2006-12-09
In my experience, the black screen plus blinking cursor usually means there's a problem between your video hardware, and the configuration file. 

See if you can get to a terminal screen by pressing CTRL+ALT+F1 or F2 or F3 ..., and if you can, edit your /etc/X11/xorg.conf file directly. It's possible Ubuntu misidentified your card, assigned the wrong driver, and as a result the video card is freaking out. ;)

Let us know how it goes.

---

