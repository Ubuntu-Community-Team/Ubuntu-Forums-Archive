---
title: "Partition sizes for various OS"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by ukeitaro on 2006-12-26
Hi everyone,

This is my first post. I am new to ubuntu and the whole linux shebang.

I will be reformatting + partitioning my 100gb hdd for the purposes of installing windows vista, ubuntu, and solaris.  How much big of a partition size should I reserve for each of these OS?  Windows Vista will be my primary OS and will hold various applications I need for school (e.g. Matlab, Photoshop, MS Office, etc.), but I will be playing around with ubuntu and solaris for fun.

I also hope to store my decent-sized media collection in a separate non-OS partition.  Are there any file format conflicts that I should be aware if I want to access these files from any OS?

Thanks for the help!  This forum looks awesome!

Mike

---

### Post by Sef on 2006-12-26
> I will be reformatting + partitioning my 100gb hdd for the purposes of installing windows vista, ubuntu, and solaris. How much big of a partition size should I reserve for each of these OS?

Vista requires at 20 gb with 15 gb free.   Ubuntu you can install with 5 gb.  Solaris requires 2 gb.  


> Are there any file format conflicts that I should be aware if I want to access these files from any OS?

If you want to share between all three oses, then use FAT32.   It is possible to use ext2, but [Paul's Software Projects]("http://paulf.free.fr/software.html") has a way , but it is not guaranteed to work.

**Back up** your files first.  There are no 100% guarantees that everything will work perfectly.

---

