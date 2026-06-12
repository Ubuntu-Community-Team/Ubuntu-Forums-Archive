---
title: "Dual boot XP and Ubuntu on two hard drives."
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by Muffinabus on 2007-06-23
First of all sorry about the stale topic, I have done quite a bit of reading on some other dual booting threads and just wanted to clarify a couple of things.

I have a 120 GB NTFS formatted hard drive running Windows XP.  I also have a 250 GB completely blank hard drive that I have yet to format or do anything with.  I plan to install Ubuntu on the 250 GB drive but am unsure of how I should partition it.  I have heard of making 1 GB swap partitions but am not exactly sure what for, anyone care to explain? What does a swap partition do?   Also, if I were to make enough space for Ubuntu by itself, say a 10 GB partition on the 250 GB drive, would Ubuntu and XP *both* be able to access the other ~240 GB as a data drive, or is there a better way to partition my second hard drive?

I have also heard that, when preparing to install Ubuntu with a dual boot, that it is generally a good idea to remove your Windows drive (unplug it), install Ubuntu, then plug your Windows drive in as a slave and show GRUB where to go to boot it.  Seems like it would be safer in the sense that it kind of guarantees that Ubuntu wont be messing with my XP drive (and I HAVE heard of some bad things happening).  Should I install Ubuntu this way?  Or should I just install Ubuntu on the second drive and let GRUB automatically detect everything?

I am just guessing here, but I believe with the Windows drive set to slave and the Ubuntu drive as master, the GRUB menu.lst file would look something like this for the Windows drive:

title        Microsoft Windows XP Professional Edition
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

Ami right?

I may have more questions, I will post them if I happen to think of any more or anything I may have forgotten.  Thanks for the help.

---

### Post by reclusivemonkey on 2007-06-24
> **Muffinabus said:**
> I have heard of making 1 GB swap partitions but am not exactly sure what for, anyone care to explain? What does a swap partition do?

A swap partition is when your hard drive is used in substitute for physical RAM. Obviously this is not ideal, but its a necessary evil. There are all sorts of ideas about how much swap you should have, but this is dictated mainly by two things; the amount of physical RAM you have, and the size of your hard drive. To simplify things for you, 1Gb will be just fine on a 250Gb drive.

> **Muffinabus said:**
> Also, if I were to make enough space for Ubuntu by itself, say a 10 GB partition on the 250 GB drive, would Ubuntu and XP *both* be able to access the other ~240 GB as a data drive, or is there a better way to partition my second hard drive?

Ask ten people how to partition a 250 Gb drive and you'll get ten different answers ;-) Linux can read/write to FAT formatted drives, and now with a little work, can read/write to NTFS drives. I also understand there is an ext2(3?) driver for Windows to read these types of partitions. Can I ask;

What sort of data will you be sharing?
Which will you use the most, Linux or Windows?

These will shape the advice I would give.

> **Muffinabus said:**
> I have also heard that, when preparing to install Ubuntu with a dual boot, that it is generally a good idea to remove your Windows drive (unplug it), install Ubuntu, then plug your Windows drive in as a slave and show GRUB where to go to boot it.  Seems like it would be safer in the sense that it kind of guarantees that Ubuntu wont be messing with my XP drive (and I HAVE heard of some bad things happening).  Should I install Ubuntu this way?


That seems a good idea to be safe. The good thing with grub is you can just add the right lines and it should all work just fine. Windows is definitely not friendly with regard to booting alternative operating systems.

---

