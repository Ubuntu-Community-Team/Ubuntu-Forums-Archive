---
title: "Deleting Ubuntu: fixed"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by derby007 on 2006-12-06
This might help someone in a similar problem: A friend of mine had a problem this morning, where he had installed a version of Ubuntu on his 'WORK PC' (which was also running Win 2000) but then wanted to delete it.... He used Win Explorer (right-click on MyComputer>Manage) to delete his partitions but ..... then found his next Boot-Up went astray. It gave him an error: Grub loading >>> error 22. I then helped him out by doing the following: Make a boot floppy, eg. Copy from 'bootdisk.com' a file called 'Boot98se.exe' or similar. Double click and choose your floppy (A disk). This gives you a boot floppy. Then set the BIOS to boot from floppy 1st. When you get a prompt: A:\ type: fdisk /mbr (ie. A:\fdisk /mbr). This may take a few seconds. Then take out floppy & re-boot. And he was restored, after an anxiety attack.
I hope this helps someone. Maybe its already on the forum, i don't know. :-D

---

