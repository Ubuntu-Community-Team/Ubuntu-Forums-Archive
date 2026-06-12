---
title: "Big problem with installing"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by Exdij on 2009-12-16
When i am trying to install Ubuntu 9.10 on same partition with Microsoft Windows Xp there is some error at the end of installation but i can't get to the log file cuz i can't see hidden folders(somethings broken when i enable that option it selfs disable:()heres the screenshot [[IMG]http://img69.imageshack.us/img69/3126/ubuntuerror.th.png[/IMG]](http://img69.imageshack.us/i/ubuntuerror.png/). When i am trying to boot from cd it doesn't see any system and load my xp. Also the option on the Ubuntu installer Demonstration and full installation isn't working ( i mean the reboot now option, nothing happens when i am using it). Maybe this happens becouse outdated BIOS? (BIOS version is on the screenshot). By the way sorry for my english:)

---

### Post by quixote on 2009-12-17
You're trying to use the wubi version that runs inside Windows, right?  If it's a regular install of ubuntu, it needs its own partition.  You can't put it on the same one with Windows.  Putting ubuntu on a separate partition and having a dual boot install is at least as easy as trying to run it inside Windows.  I'd say easier.  You may want to partition off 10-20GB of your hardrive and download and try regular ubuntu?

Even though you can't see hidden files, I wonder if the following might work.  Open a terminal (I think it's under Accessories and "MS-DOS") and type c: cp c:\documents\great-long-hidden-file-name-copied-as-on-screen c:\documents\whatever-the-path-should-be\new-unhidden-file-name.

---

