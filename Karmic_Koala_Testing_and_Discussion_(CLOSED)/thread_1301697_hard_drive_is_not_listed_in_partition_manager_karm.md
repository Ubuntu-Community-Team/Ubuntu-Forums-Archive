---
title: "hard drive is not listed in partition manager karmic rc"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by angryhomer17 on 2009-10-26
The partition manager on the Xubuntu 9.10 amd 64 desktop cd does not show /dev/sda as a choice for installation. My other two hard drives do show up. 

I am trying to do a fresh install of karmic on sda after having upgraded to karmic beta on the same drive. I had some previous messed up settings I didn't want to worry about.

I've tried using the alternate cd, wiping the drive, reformating, repartitioning, etc and I can never find sda with the partition manager. sda is listed under fsdisk, it does have a valid partition, it shows up in gparted, and I can generally access it without a problem.

I've tried installing 9.04, which does show sda, but fails with a grub 22 error after install. 

There are two possible problems that I see. One the drive is showing up as raid, even though it isnt. (The drive came with promise-realtek raid software, but I don't use it. Also, the drive is hooked up like any standard sata drive) The alternate installer says that I have raid devices on the machine, would I like to show them. Saying yes or no does not show sda.

Two, the drive has some bad sectors. Palimpset says 68, which shouldn't be enough to corrupt the drive entirely.

So, how do I install 9.10 on /dev/sda1? Either from cd, or using the 9.04 cd and upgrading from there (although I will still have the grub 22 error) Thanks.

---

### Post by paul8472 on 2009-10-27
I have a very similar problem (I think).  I've just filed it as a bug in 9.10 as it didn't cause a problem in 9.04.  Details are here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470)

---

### Post by angryhomer17 on 2009-10-27
Well I got karmic installed on sda1, but had to install 9.04 first, and then upgrade. I wiped the drive and 9.04 installed without any grub errors.

Before I installed 9.04, I removed an old IDE cdrom drive, which may have been causing problems. Also, this BIOS reports that I can boot from a removable device (i.e. USB) now. I haven't had this option before, and haven't ever flashed the BIOS. The BIOS will boot from USB, which is nice, but I'm not sure how I got that option.

9.10 never did show sda1 though.

---

