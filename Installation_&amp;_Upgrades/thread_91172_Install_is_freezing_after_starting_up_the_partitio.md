---
title: "Install is freezing after starting up the partitioner"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by boedeker on 2005-11-16
[!!] Partition disks
     ???   ???

<Go Back> <Continue>

wont go on from here. i did create a new partition before installing with partition magic, because i wanted a small windows partition for a few programs. any help?

---

### Post by boedeker on 2005-11-16
so i just deleted the new partition i created, and now its hanging up in the same spot as before:

Starting up the partitioner
52%

---

### Post by boedeker on 2005-11-16
any ideas. for the late night crowd? windows 98 is the current os

---

### Post by aysiu on 2005-11-16
Can you explain exactly what you're doing? Your first post is very cryptic.

---

### Post by boedeker on 2005-11-17
sorry, cause the replys are out of order kind of.

ok so i have a dell inspiron 3500 with windows 98 on it.

my intention was to download the cd image for ubuntu and install it.
i tried this, but when it got to partitioning drives it hung up at 52%.

at this point i decided that i really wanted a small windows partion so i installed partition magic and created a new partition.

then i tried to install ubuntu. it got past 52% but then i got the error at the end of the partitioning drives segment with the three question marks. it asked if i wanted to <continue>, if i select this is just flashes then brings me back to that screen. it does the same if i select <go back> 

so i removed the partition. and now its hanging at 52% on the partitioning drives screen.

---

### Post by aysiu on 2005-11-17
You may have two separate problems:

1. The installer disk you're using might be corrupt (hanging at 52%)
2. The newly created partition may have some of its own corruption (???)

Before you burned the disk did you [do a checksum](http://www.linuxiso.org/viewdoc.php/verifyiso.html) on the ISO (disk image)?

When you burned the disk, at what speed did you burn it?

As for the possible corruption of the partition, I don't know what to tell you there. I've never had that problem.

---

### Post by boedeker on 2005-11-17
ok so i:

1. checked the MD5sum and it was the same.
2. i re burned the install cd at a slower rate. still hanging at 52%.
3. i formatted the harddrive and reinstalled windows 98. still hanging at 52%.

ahhh.

---

### Post by az on 2005-11-17
Well, if you are going to reinstall anyway, you can wipe your partition table.  Windows partitoining tools bugger them up all the time.  Use fdisk to start with a blank partition table.

Then, create a fat32 partition for windows (I think it can do it by itself, but I am not sure) and install windows.

Then inster the Breezy cd and install.  It should be able to shrink the existing windows partition and create free space by itself.  the reason I guess it is not working for you right now is because you used another tool to do it and it screwed up your table.

There may be a way to fix the partition table, but I do not know right now.

---

### Post by boedeker on 2005-11-17
Yeah I thought the same thing, thats why I re-installed windows - starting with fdisk and i still am hanging up at the same spot. I'm temped to format and install ubuntu and then go back and install windows later is this possible?

---

### Post by az on 2005-11-17
Yes, but you will have to chroot back into the ubuntu install afterwards and run

grub-install after you add windows to the boot menu.list.

---

