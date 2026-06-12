---
title: "[SOLVED] Fixing a Live USB pen drive after installation of Ubuntu"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by TheZergcorp on 2008-11-23
So, my girlfriend recently got an Asus eee PC, and the Xandros kernel that ships with it has tested poorly against other distributions, and was certainly too slow for her needs. Without a CD drive, however, I had to create a live pen-drive rather than use any of my live CDs. 

First, I used the instructions found [here]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/") in order to create an installable version we could run off of one of her USB ports. Not realizing what they meant by "Persistent," I didn't realize I was putting ubuntu on a pen drive instead of making it installable. Pretty cool mistake, though.

Secondly, I used another pen drive (the first one wasn't quite large enough to begin with) and went through the steps on this [documentation page]("https://help.ubuntu.com/community/Installation/FromUSBStick") in order to actually install what I wanted. Long story short, her eee is now working perfectly, however I can't for the life of me figure out how to now remove the live partitions off of the flash drives in order to use them normally again.

I have tried going back into both using the fdisk command in the terminal and deleting the partitions, which seemed to delete the data on the pen drive, however the "persistent" variant still mounts as two different partitions, "Ubuntu8" and "Casper-cw." On the other hand, the live flash drive simply mounts as "live" but doesn't want to listen to me when I tell it that I am a super user, and yes, it does need to delete all of the data it currently has.

I saw a method on the pen-drive linux site for zeroing out all the data on a flash drive, however I don't know if it will fix my double-mounting problem for the first one, or how risky it is in general. 

Any help would be greatly appreciated.:confused:

---

### Post by C.S.Cameron on 2008-11-25
Casper-rw partition can be a hassle.
If the thumbdrive containing it is plugged in before booting the Live CD it's persistence is often seen by the CD and it becomes invisible, the same as a home-rw partition.
I have been able to delete it using gparted from the Ubuntu Live CD, I prefer using the Gparted Live CD when dealing with this partition.
I would suggest deleting all of your partitions then formatting in FAT32, Windows sees this just fine.
Do not try formatting a multi partition flash drive with the Windows partitioner, It only sees the first partition on a flash drive, and can end up bricking it, (I've done that twice).

---

