---
title: "Ubuntu 11.10 installation failed through USB drive"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by unclesam.xu on 2011-10-31
Hi, this morning I posted a post, it seems ubuntu 11.10 won't show grub menu after installation. this bothers me all day , Now this is the real problem.

I tried 32 bit or 64 bit, if I install to first partition, it will say "missing operating system" after installation -> restart. If I install to second partition ( save the first for win 7), it will say "bootmgr is missing" 

I don't have a CD drive yet, I use either unetbootin or ubuntu 10.10's usb creator to make a live USB disk, the live USB can run by itself, but after install , then restart, computer shows the message above.

I ordered a USB DVD drive but it is backordered. I did some reading , other people have same isue out there but  no answer for it.

sigh

---

### Post by fantab on 2011-11-01
> **unclesam.xu said:**
> Hi, this morning I posted a post, it seems ubuntu 11.10 won't show grub menu after installation. this bothers me all day , Now this is the real problem.

I tried 32 bit or 64 bit, if I install to first partition, it will say "missing operating system" after installation -> restart. If I install to second partition ( save the first for win 7), it will say "bootmgr is missing" 

I don't have a CD drive yet, I use either unetbootin or ubuntu 10.10's usb creator to make a live USB disk, the live USB can run by itself, but after install , then restart, computer shows the message above.

I ordered a USB DVD drive but it is backordered. I did some reading , other people have same isue out there but  no answer for it.

sigh

**Install GRUB on /dev/sda** , and **not** on the partitions like /dev/sda1 or /dev/sda2 , etc.

---

