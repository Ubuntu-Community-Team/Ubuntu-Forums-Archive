---
title: "Wubi 11.04 Installation Error"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by nicotek on 2011-09-25
Hello Everybody,

This is my case.

I have a pentium 4 with win7 64bit with a hardware raid.
for about a year i had wubi with ubuntu 10 running fine.

I decided to for 11.04. so I unistalled wubi from win and then run the new installer.

the installer finished fine in windows and then asked for reboot.
once it reboot I chose ubuntu in the bootloader.

The desktop background of ubuntu appears, and says finishing installation. then i get the error "No root file system is defined. Please correct this from the partitioning menu"

any ideas on how to get through this?
or why the previous version worked and not this one?

Many Thanks!

---

### Post by RJBarber on 2011-10-11
have you gotten an answer to this question? I am running windows xp. I dowloaded ubuntu and burned it ti a cd. It runs fine from the CD. When I try to install it using Wubi I get the same problem you do. I have searched the web and have not found a solution to this problem. Have you got it running yet?

---

### Post by bcbc on 2011-10-11
Probably a partition table error that's not significant but the Ubuntu installer (and tools it uses) is less tolerant. Best to boot the live CD and run the [bootinfoscript ]("http://bootinfoscript.sourceforge.net/")to see if that gives any clues.

---

