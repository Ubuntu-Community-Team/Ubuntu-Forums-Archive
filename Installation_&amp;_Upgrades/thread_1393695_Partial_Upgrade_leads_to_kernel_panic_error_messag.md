---
title: "Partial Upgrade leads to kernel panic error message"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by RedOctober22 on 2010-01-29
I got a notification that there was an upgrade available today in ubuntu 9.10 64, after the update i restarted my system and while booting i encountered this error message:

Kernel panic - not syncing : VFS : Unable to mount root fs on unknown - block (8,17)

does this have something to do with the OS looking at the wrong hd?
theres no command prompt to actually do anything and i tried booting in safe mode and had the same problem. Let me know what i can do! 
THanks

---

### Post by Revolutionary101 on 2010-01-29
Sounds like you will have to reinstall Ubuntu. Thats a bummer. If GRUB could not find the OS it would have something along the lines of "Could not find OS" or something like that. I have messed up GRUB a few times and I have had the problem of GRUB not detecting the OS.

---

### Post by shahani.w on 2010-01-30
I had the exact same problem after the updates that were installed 29/01/10 (and a subsequent reboot).

Re-installation is not necessary.

Follow the steps given in [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

I did not need to do the editing in step B. It worked fine when I just copied the wubilder file to the C: location.

---

### Post by Gypsygirl on 2010-12-01
I am having similar issues with my Ubuntu.  I know almost nothing about ubuntu.  A friend put it on my PC for me.  I do not quite understand from the things I've read how to fix the error message.  Mine reads Kernal panic not syncing VFS Unable to mount root fs on unknown block 0,0.  I did not add all the dashes and brackets etc.  If some one can explain to me how to fix this in very basic terms I would be very greatful.  Also if you could email it to me would be better as I have no idea how to get back to this forum.  Thank you very VEERY VERRRREEEERRRYYYYYY much!:popcorn:

---

