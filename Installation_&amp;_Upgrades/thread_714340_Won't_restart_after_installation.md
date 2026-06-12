---
title: "Won't restart after installation"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by Jay2008 on 2008-03-03
Hi,

Any help or suggestions are appreciated.

I had some initial problems with the install on for 7.10, but eventually the dowloaded copy I am using brought me through the full install.  It completed the initial restart, but after getting the updates, it fails to start again....

It hangs at the ubunta start screen, with only a sliver of orange on the download bar, then fails to this messaging after about three minutes:

[I]BusyBoxv1.1.3 (Debian 1:1.1.3-5ubuntu7)

(initramfs)  [    226.001521]  ata 3.00: exception Emask 0X0 SAct 0X0 SErr 0X0 action 0X2 frozen[/I]

It then spits out a few lines of similar information every 20 to 30 seconds later, and followed by:

*Buffer I/O error on device sde, logical block 0*

The searching I have been doing leads me to believe that the system is having difficulty finding the initial files to start the operating system.  I have run the meory test with no errors listing, and have also tried to re-install with the same results.  Frustrating that it worked from the LiveCD and the install, but is now unable to load.

Once again, any help would be appreciated.

---

### Post by dstew on 2008-03-04
There may be a disk problem. From the Live CD, run the program fsck on the partition that Ubuntu was installed to. If it was installed on /dev/sda1 do **fsck -a /dev/sda1**

---

