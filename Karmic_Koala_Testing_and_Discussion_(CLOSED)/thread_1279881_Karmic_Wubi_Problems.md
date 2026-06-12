---
title: "Karmic Wubi Problems"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vishy1618 on 2009-10-01
Hi, I recently (a day ago) downloaded the daily Karmic build and installed it "inside windows". The installation went without any hiccups, but, now when I select the "Ubuntu" entry at startup it says:

Try (hd0,0): NTFS 5

Then it drops me to a grub prompt. This leaves me with a unusable ubuntu installation. Please show me a way to solve this. This is a Wubi bug, I think.

---

### Post by vishy1618 on 2009-10-01
Any one had problems with this in Karmic? Please reply.

---

### Post by wilee-nilee on 2009-10-01
I am not an expert in this but I wonder if the Ext4 does not want to play with windows it is also a beta release. You would have a safer faster set up to dual-boot, that is if you like Ubuntu. The possible danger of running Wubi is that although a virus may not effect the Ubuntu setup if you get it working but it can head on over to windows.

---

### Post by vishy1618 on 2009-10-01
It is not a matter of liking Ubuntu, I like Ubuntu and have been using it for the past year. However, on this laptop, I am not permitted to make a partition and a dual boot installation. My father would kill me! However, this is the only fast computer I have access to, and it is really a shame to waste this hardware on Windows XP. Note that jaunty and the others ran fine on this hardware (WUBI or LiveCD)...

Has this problem been fixed in the latest build? Thanks for replying!

---

### Post by vishy1618 on 2009-10-01
Also, at the grub prompt I can do an ls and it detects all my hard disk partitions properly. I can even "root" into the primary NTFS partition (where Ubuntu is installed). Any thoughts?:(

---

### Post by ubnoobie on 2009-10-22
> **vishy1618 said:**
> Any one had problems with this in Karmic? Please reply.

yes. saw that when trying to install 32bit karmic BETA (using wubi as provided by BETA desktop cd image) in 32 bit vista on a dell desktop (amd/nvidia) w/ 4gb ram and 4 existing partitions on the sole hdd (first two of which are hidden dell diag and recovery partitions). vista OS is on third primary partition (first visible), and that was also the target for the ubuntu files during the wubi install.

this was **after** i had to drop the system memory down to 2gb (from 4gb) just to get the install to progress past checking partitions.

---

### Post by jdjennings on 2009-10-27
Happened to me this morning.  I did an update/upgrade yesterday and powered off my laptop.  Powered it up this morning, and got the same:
Try (hd0,0): NTFS 5
and then a grub prompt.

I reinstalled everything this morning, and again did an update/upgrade.  Now I get a the grub menu that shows my Ubuntu install, but when it boots I get a kernel-panic that VFS can't find the root filesystem.

---

