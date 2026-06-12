---
title: "The absolute worst partitioner/fstab - the winner is Ubuntu"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by mrfelker on 2007-08-23
I've complained about the partitioner before - you have to ignore LOTS of warning about incompativle file systems etc.

But the very worst thing (worse than ANY distro I've installed) is the fstab which has the UUID instead of a straightforward /dev/Hdx listing.  Because of this drives appear on the Desktop and cannot be deleted.  Whatever you don't try to edit FSTAB - you will regret it!

If the developers read this I ask you why to thought to add UUID references to all drives.

Please remove this "feature" in future Ubuntu distros (obviously AFTER Gutsy).

Actually, I'm fulminating about this.

---

### Post by maybeway36 on 2007-08-23
What's "the partitioner"?

---

### Post by mrfelker on 2007-08-23
That the program at the beginning of the install which shows you all the partitions on the drive and you can choose which one to install.  You don't see this if you do a "normal" install from the Ubuntu desktop - only when you use the Alternate install (not for many since it is a text installation)

---

### Post by Azzco on 2007-08-23
What's wrong with the fstab?
I've never seen anything like that on my desktop.

You might not believe this but using UUID can have good sides too.
What if you were to buy a new HD and really wanted it to placed as master instead of slave. If you'd then boot up ubuntu and it wouldn't use UUID would everything be mounted right? Wouldn't your old HD be placed as secondary HD? (aka /dev/hd(or sd) b) and be mounted all wrong.

---

### Post by adewale on 2007-08-23
Well i never understood the UUID stuff but i guess its for a good purpose, as i read some stuff on it on the forum sometime ago.
I once had a problem with my swap not mounting everytime i boot up, i have to manually mount it using gparted, so i got tired of this and edited my fstab adding an # infront of the swap UUID then ran sudo fdisk -l to know what my swap was and entered it manually in the fstab and it works without any problem

---

### Post by dabl on 2007-08-23
Hmmmm.  I have:

1 IDE hdd
4 SATA hdds
1 IDE CD/DVD drive
1 webcam
1 SD card reader
2 thumb drives (but only 1 at a time)

3 Linux OS's,
1 Win XP

All booting from the same Grub boot menu, and happily co-existing.  Based on my recent experience adding the last SATA hard disk drive, I don't think it would have worked without the UUID system -- too much confusion with those USB devices coming and going from the USB bus.

Just use gedit to edit fstab and menu.lst, or kate in Kubuntu, or scite in e-live.  It's no big deal -- works just fine.  Really, it does.  :guitar:

---

