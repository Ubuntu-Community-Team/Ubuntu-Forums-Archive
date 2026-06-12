---
title: "Ubuntu 7.1 -- I've lost everything!"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by togo59 on 2007-11-01
I downloaded the ISO and checked the MD5 and ran a file integrity check prior to booting in M/C below.

Installed Ubuntu 7.10 for first time on Viglen PC previously running XP professional. Has single 200 Gb disk, Intel chip.

Started installation. Accepted default boot partitions. Rebooted. As it shut down I got a screenful of errors (scrolling too rapidly to write down but lots of "corrupt" this and that) finally removed CD.

Result no OS. No Windows OS and no Ubuntu. Tried different boot drives (could see the partition) in the BIOS. Still nothing. (Thank G. I backed up my data first!)

When I boot from the CD now, all the text in the menus is little squares! So I can't read any of the menus!

Firstly, how do I recover Windows? At least then I can install Partion Magic and remove the Ubuntu partition.

BTW: I use SUSE Linux (now 10.3) dual booted on my lap-top with XP and no problems at all. So far I give SUSE 9/10 an Ubuntu minus several zillion out of ten. But I am willing to be persuaded. It looked good for a while.

I can't give you much more as the computer concerned is totally dead. 

Please help!!

---

### Post by be4truth on 2007-11-02
If you have a Window XP CD you can use this to recover your master boot record. Boot the XP CD into repair mode and type 'fixmbr'. The administration passwd is often not set (just press enter).
Afterwards you can go into Windows administration tools and delte the Linux partition (2 numbers - 1 swap and one ubuntu).
I installed recently 7.10 Gutsy and had problems with 2 computers. Feisty 7.04 runs very smoothly. You could try the alternate CD to install Gutsy. This uses a text based installation interface. When you download it set the checkmark at 'alternate CD'
OpenSuSe is good but Ubuntu has no commercial alternative. All the goodies are here! And a fantastic community for support.

---

