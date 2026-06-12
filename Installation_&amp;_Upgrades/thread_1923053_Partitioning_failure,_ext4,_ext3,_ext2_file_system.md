---
title: "Partitioning failure, ext4, ext3, ext2 file systems can't be created."
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by northfly on 2012-02-09
> **hexavi42 said:**
> I just tried it after reading your post. Unfortunately, it doesn't work. It just stopped at 5% and the error message (word for word) was "The attempt to mount a file system with type ext4 in SCSI1 (0,0,0), partition #1 (sda) at / failed. You may resume partitioning from the partitioning menu.". What should I do? I've tried manually partitioning it before (I think) after the third or fourth time that it failed to mount the file system.
t I got
edit. I tried the sudo fdisk thing through terminal while I was running ubuntu from the cd. this is what i got.

Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x6ad856c9.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 2434.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)
I got exactly the same problem, I don't what happened actually, maybe after a normal header update or something, and reboot and there is no OS found, and try to install a new one, and then this 5% cannot create ext4 problem happens every time. so what I can do? is there any standard procedure to solve this?

---

### Post by oldos2er on 2012-02-09
Post moved to its own thread.

---

### Post by northfly on 2012-02-10
I solved this problem, here is how I did it:

1, install my problem harddisk to a new computer
2, use alternative cd to install ubuntu on that new computer and that problem harddisk
3, when installing, set scs1 as bootable, remove the 5% reserved space
4, reinstall the hardisk to your original computer and reinstall again

here we go, enjoy!!!

---

