---
title: "Dualbooting Linux across multiple drives"
date: 2016-09-08
forum: MINT
---

### Post by bobapplepie on 2016-09-08
I am installing Linux Mint alongside Windows.  I have both a ssd and a hdd; I would like to use the former to put the OS and some programs on and the latter to use as mass storage.  I have made some free space on both.  When I install linux, how should I divide them?  Should I put home, root, and swap areas in both?

---

### Post by QIII on 2016-09-08
Moved to the MINT sub-forum.

---

### Post by yancek on 2016-09-08
> Should I put home, root, and swap areas in both? 		

On both drives?  No.  You just need one partition for the root filesystem and maybe a swap which can be on either drive, depends on the physical RAM you have.  You can also create  a separate home partition, that's a personal choice.  You could also just use the root partition and create a data partition during or after the install.  Again, a personal choice.
Which drive is windows on?  If the SSD, how big is it?

---

