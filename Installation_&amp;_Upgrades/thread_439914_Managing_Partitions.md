---
title: "Managing Partitions"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by psychoadonis on 2007-05-11
Hi..

I'm new and have taken a bold step by removing XP completely and installing only Ubuntu. I don't remember what happened during the installation, but now in places, I see "Computer". In that, there are my other removable drives, and the "Filesystem".

I want to know how I can make partitions (like in windows) to keep my data safe, and have the option to format the system partition if I have to.

---

### Post by Compyx on 2007-05-11
You can use 'fdisk' to manage partitions, the safest way is by running it from the LiveCD.
Formatting partitions can be done with the appropriate tools, such as 'mkreiserfs' for ReiserFS, 'mke2fs' for Ext2 (or Ext3 when passing the option '-j'), and so forth.

After having created and formatted your partitions, you'll have to alter the file /etc/fstab and add the partitions with the appropriate mount points.

There's also a tool called 'gParted', which (if I recall correctly) allows you to resize partitions, it's a GUI-tool. I haven't used it for years, so I'm not sure how well it performs.

This page from the Gentoo Handbook: [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4") might give you some idea how to create and manage partitions. Of course it's written for Gentoo, but it should give you some hints.

---

### Post by psychoadonis on 2007-05-11
> **Compyx said:**
> You can use 'fdisk' to manage partitions, the safest way is by running it from the LiveCD.
Formatting partitions can be done with the appropriate tools, such as 'mkreiserfs' for ReiserFS, 'mke2fs' for Ext2 (or Ext3 when passing the option '-j'), and so forth.

That sounds like I might have to use the terminal. So before I try that, is there something like Powerquest Partition Magic that I can use?

---

### Post by ajgreeny on 2007-05-11
You could have made a separate home partition at install if you wanted by chosing the manual option at partitoning, but if you want to change to that now the instruction are available in the forum if you search.

---

### Post by Compyx on 2007-05-11
> **psychoadonis said:**
> That sounds like I might have to use the terminal. So before I try that, is there something like Powerquest Partition Magic that I can use?

Yes, gparted is somewhat like partition magic.

---

### Post by psychoadonis on 2007-05-11
Hi,

I tried searching for gparted. I guess its now called "GNOME Partition Editor". And you're right... it does look like Partition Magic. But the thign is that I dont think it can work much from within the OS. 

The option to resize/move the partition with the OS is greyed out. Actually, all options are greyed out except for unmount.

Is there a way I can use GNOME Partition Editor from the Live CD? Or some other way through which the options are now greyed out?

---

### Post by ajgreeny on 2007-05-11
Use the live ubuntu CD or download the new version of gparted liveCD from sourceforge.  It's really great for doing any partition jobs you have and has never let me down.

---

