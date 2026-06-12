---
title: "Dual boot XP Gusty - necessary to create a shared partition?"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by mandz on 2008-01-20
Hi all,

I know there have been a few similar threads on this but they're all pretty old in computing world terms and I'm sure there have been some developments.

Very simple question (I hope!): I'm dual-booting my PC with Ubuntu and XP - is it entirely necessary to create a shared partition? Its purpose would be to shared multimedia files between the two, and I need to keep XP mainly due to Windows Digital Rights Management on TV streaming. For now, I would like to keep my photos available for safe read/write in both operating systems for convenience.

I have had a dual boot set-up for quite a while, and I have been using the /home partition as the shared one between the XP and Ubuntu by using the fs-driver in XP (probably not ideal but I'm learning!). However, this seems to have damaged the file system and Ubuntu fdisk doesn't fix it. I don't want this happening again.

So... I'm going to re-install Ubuntu and start afresh after rescuing my files - is the NTFS-3g read/write reliable enough now to simply make my Windows partition the largest and read and write multimedia files in Ubuntu to the NTFS partition instead of creating a separate shared one? Or is there another option I haven't thought of? As the shared files will chiefly be photos and memories, I need it to be reliable (and I'm sure you'll say you should always back up important files but one doesn't always get around to taking back-ups as frequently as is ideal!).

Your help is much appreciated. Thank you!

Mike

---

### Post by Pumalite on 2008-01-20
Try ntfs or vfat (depending on the size of your files)

---

### Post by jnorthr on 2008-01-20
my feeling would be to make one new common partition as fat or fat32 cos both os would be able to use it as they have done succesfully now for a few years. you could allocate it as /usr/local. Then make the usual /swap / root and /home partitions. then stuff all the music, photos etc under /usr/local 

before spending hours reloading music, etc just reboot and confirm xp will 'see' the /usr/local maybe write one file to it in xp then read it in ubuntu. It would be easier to backup too when you get around to it.  :-?

---

