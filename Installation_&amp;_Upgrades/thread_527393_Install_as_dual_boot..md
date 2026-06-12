---
title: "Install as dual boot."
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by Newuser1111 on 2007-08-16
How do I install ubuntu to dualboot with Microsoft Windows XP Home Edition Version 2002 Service Pack 2?
Safely?
On a Acer Aspire 3000 Laptop?
The Live CD works.
Also, Why isn't the wireless working?
On the CD is Ubuntu 7.04 i386.

---

### Post by fumduck on 2007-08-16
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

[http://apcmag.com/dualboot]("http://apcmag.com/dualboot")

there are step by steps to read..  I'd also google  your laptop to see what (if any) issues people might have had installing to your particular laptop.

Good luck.

and make sure to back up your important data

---

### Post by dabl on 2007-08-16
Here's more to know: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

:)

---

### Post by Newuser1111 on 2007-08-16
Do I have to backup the D drive?

---

### Post by onthegojohn1234 on 2007-08-16
read my post in this forum: [http://ubuntuforums.org/showthread.php?t=527334]("http://ubuntuforums.org/showthread.php?t=527334")

make sure you keep your XP on the first partition, otherwise it might not boot.

---

### Post by Newuser1111 on 2007-08-16
Do I have to backup windows?
Does having all drives be FAT32 affect anything?

---

### Post by merlinus on 2007-08-16
Back up your personal data.

Before attempting to install ubuntu, delete temp and unneeded files, set virtual paging to zero (set it back after install), and defrag several times.

Then at the ubuntu partitioning menu, select resize first partition and use freed-up space.

-merlin

---

### Post by Patrick793 on 2007-08-16
The easiest way to Dual Boot with Windows, and safest, is use [Wubi Installer]("http://wubi-installer.org/"). It does no partioning. It creates a file, which acts as a virtual Hard Drive. And It adds a file to the Boot folder, so you can chose between Windows, and Ubuntu. It works really well. That's how I got Ubuntu installed.
It's been tested and works on Windows 98 to Windows Vista.

---

### Post by Newuser1111 on 2007-08-16
Does haveing all drives being FAT32 affect any thing?

---

### Post by merlinus on 2007-08-16
The ubuntu installer will ask to change its partition to a linux filesystem.  You get to choose which, but ext3 is probably best.

xp can remain fat32, or you can convert it from within windows to ntfs without losing any data.

-merlin

---

### Post by dabl on 2007-08-16
> **Newuser1111 said:**
> Does haveing all drives being FAT32 affect any thing?

Yep, it keeps you from running Linux.

Your partition where you want to install Ubuntu needs to be ext3 or reiserfs.  :)

---

### Post by Newuser1111 on 2007-08-17
Everything went to perfectly.

1.Didn't backup anything and nothing got deleted!
2.Ubuntu was installed and windows is still there! Both working!
3.No problems!

---

