---
title: "Reinstall / double install"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by ascus4 on 2007-04-18
I have reason to convert my 64 bit Ubuntu install to 32 bit without messing up my WindowsXP partition. The last time I to reinstall Ubuntu in this manner I ended up with one Windows and two seperate Ubuntu installs on the same machine. 

I guess I messed up in partition manager during install.  Maybe my mount points, who knows.

I need to do this.
Any ideas?

Thanks folks,

W

---

### Post by Voland on 2007-04-18
As I understand, you want to delete 64-bit version and install 32-bit. So try to delete your Ubuntu parition, format and make a free space on it. Then start installation and choose "Use unused free space on partition". Your Windows partition will be OK, if you detele only Ubuntu partition.
P.S. Save your profile information (/home/user_name)

---

### Post by ascus4 on 2007-04-18
I thought about doing that from Partition Magic on the Windows side.

---

### Post by Voland on 2007-04-18
Any partition manager will be suitable.

---

### Post by ascus4 on 2007-04-18
I'm in the Ubuntu live CD install menu as we speak.  I have the partitioner open and am looking at it.

dev/hda1 is NTFS so that is my Windows partition.
dev/hda2 must be linux with hda5, hda6 and hda7 being linux-swap, reiserfs and reiserfs.

The next page allows for setting of mount points.  It has four of them,  /media/hda1, swap, /media/hda6 and /media/dha7.  The /media/hda1 must be Windows again.

So...I guess the short version is.....HELP.  What do I do now?????

Tnx

---

