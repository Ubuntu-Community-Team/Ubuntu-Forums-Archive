---
title: "upgrade 9.10 to 10.04 woes"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by Bunny Boy on 2010-08-13
After the several hours of downloading files, the installation of 10.04 on my Dell Inspiron 1100 completed but then failed on reboot.  

Here's the error message:

*[    0.771387] kernel panic - not syncing:  VFS:  Unable to mount root fs on unknown-block(0,0)..*

Recovery mode does not work. 

What really blows my mind is that it messed up my Windows partition too!  It has rendered this machine completely inoperable. 

Do I have any recourse but to reinstall 9.04 from disk?

---

### Post by lemming465 on 2010-08-15
Does your BIOS have software RAID turned on?  That is a typical way to get horrible disagreements between windows and Linux over the disk layout.  You may have to wipe the partition table and reinstall both.  I get the best dual-boot results from a three step process of:
1) partition the disk using a live CD
2) install windows
3) install linux

---

