---
title: "window partiton issue with ubantu 5.1"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by hollowhead on 2005-10-16
Someone gave me a copy of ubantu 5.1.  I decided to install it over my RH9 distro.  My system consists of a primary windows partition C: and two extended partitions called D and E.  These take 3GB each leaving about 29GB which was used for RH9.  After installing Ubuntu I could not boot to windows getting an invalid system error.  I could boot to windows or ubantu using my Grub floppy created during installation.  When I got into windows all was not wll none of shortcuts to drive D worked.  This was there were now 4 windows drives rather than 3.  C, D, E and F.  D was "not formatted" C and E were as before but the contents of D were now in F:  obviously the CD drives had all shuffled up the alphabet as well.  Using Fdisk /MBR had no effect but examining the partition table was very interesting, instead of having 3 dos partitions and a non dos partition I had 3 primary dos  although one was an unknown file system thus;

c: 1 pri dos  MS_dos6 3091 Fat32
d: 2 pri dos               3004 unknown
    3 ext dos              29071 
e:  pri dos    Drive$E   2996 fat32

So ubantu was being seen as an extended partition of drive D!!???  No drive was active which is why it could not boot to windows w/o floppy or grubdisk.
From ubantu all I could see was 3 FAT drives although I could not gain access to them.

The installation was fairly painless but I did have problems using the partition manager.  In the end I let it set up the partitions as default (one / and a swap).  It didn't strike me as very initutive (bear in mind I've installed slackware, suse, RH5,6 and 9 in the past).  RH9 diskdruid wouldn't let me do what I want but choosing default partitioning worked a treat leaving windows alone.  I did have one glitch during installation that was one the installation program told me to reboot taking my grub floppy and ubantu CD out I ejected the CD but did not remove it so when the system rebooted it went into the CD and straight into the installation routine again and I went through some parts of it again before I tried rebooting and it took up where it left off.

My question is not how I restore windows to health (necessary for good maritial relations) since I've done this (using firefox in windows to write this) but when I reinstall ubantu how do prevent the same problem happening again?

Please help is it possible for someone to tell me how to set my linux partitions manually in the ubantu partition manager?  What did I do wrong?

---

