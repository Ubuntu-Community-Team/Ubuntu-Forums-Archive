---
title: "Error when installing updates"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by howardavatar on 2007-09-30
After installing Ubuntu I was told to download 120 updates.  I did then the PC locked up 15% through.  Now on reboot I get the folling error from upadte manger:
Software index broken
It is imposible to install or remove any software. Please use the package manager "Synaptic" or run "sudo -apt-get install -f" to fix the problem.

When I try the 1st sudjestion I get:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

The 2nd gives
sudo: please use single character options

Also I have ani ATI radeon X1900 video card.  How do I load drivers to get resolution above 800*600.

---

### Post by dagvei on 2007-09-30
Hi howard! I had the exact same problem last night; it was solved from a tip here on the forum: You simply  open a terminal (you find it under Programme-meny to the upper left, under acc or something) and you type "sudo dpkg --configure -a". You will then be asked for your password, and the install process will continue and fix the bugs that caused it to stop in the first place. When this process is finished, you will again be reminded of the rest of the instals, and it will work automaticcally again, when you alloud the downloads.

I hope this will work as smooth as it did for me!

---

