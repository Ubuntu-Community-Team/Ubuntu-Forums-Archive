---
title: "&quot;No Root File System is Defined&quot;"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by nulrich on 2010-01-10
Hi this is my first posting due to the following error message while trying to load Ubuntu onto a Toshiba laptop.

The Message is:
"No root file system is defined, please correct this from the partitioning menu"

This comes after i have used WUBI to load Ubuntu and it starts to install. Then it hits this error message and the only thing that I can do to get out of this is to hit the start button to close the laptop down. Any ideas please.
Nick

---

### Post by Sef on 2010-01-10
How are you installing Ubuntu?  If you are installing manually, then you need to set the root parition.  Before telling it you are done, you can set the partition to root (at top.)

---

### Post by llawwehttam on 2010-01-10
Personally I think WUBI causes more problems than its worth. If you are just trying ubuntu out then I prefer to either run it in a separate partition or run it inside virtualbox. 
Also virtualbox is much safer.

---

### Post by SecretCode on 2010-01-10
After starting wubi, accept all the defaults. It should create you a virtual partition of I think 10GB, and use all of it for Ubuntu.

---

### Post by nulrich on 2010-01-10
Thanks for the replies. I am using WUBI and its defaults. I have plenty of spare harddisk and its been defragged. I've tried loading 3 times with the same error message each time. I think I will revert to manual and see if that works.

---

### Post by SecretCode on 2010-01-11
Seems odd.

When you get to the partitioner during the install, do it manually as you say and make sure you are partitioning an 8 or 10GB partition, that you format it as ext4 (or ext3) and that it is mounted as /

---

