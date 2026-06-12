---
title: "[SOLVED] general questions about dual boot"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by &amp;wP*!) on 2006-12-03
I am trying to install Ubuntu 6.10, but before that I am trying to understand the mechanisms of a dual boot system of Windows XP and Linux.

so far I have understood from the zillions of information around the web is, that:
- it's best if we have partitions in following order:
[LIST]
[*]any windows partition
[*]swap (about 2 times the size of RAM, this partition must be first in the order to get the best performance)
[*]/boot (to install Grub)
[*]/ (root partition)
[*]/home (keeping it separately is useful when switching from one distro to other, without losing personal data)
[*]any partition
[/LIST]
- grub must be installed on a **/boot** partition
- its configuration data must be **grub.conf** (I think it also will reside in **/boot**)
- and its data must be copied as a file (e.g. **grub.bin** created by **dd**) to be saved in **c:\**.
- **boot.ini** of Windows XP must include the last entry as **c:\grub.bin="Linux"**

Now my questions:
[LIST=1]
[*]There is no clean information around whether swap must be first in the partition order. Is it necessary to do so?
[*]**grub.conf** includes entry for Windows, but Windows XP's **boot.ini** also has an entry for Linux. Why? Why does **boot.ini** show Linux and **grub.conf** shows Windows? Why do we need definitions in both directions? Won't it be enough to have one of them only?
[*]Supposing that I have done the whole stuff in the previous question. When booting a PC, how is the boot phase running? Is the boot.ini read, then GRUB is called?
[*] I have following partitioning now:
[LIST]
[*]c: ntfs (40 GB, windows xp)
[*]d: ntfs (20 GB, empty)
[*]e: fat32 (16 GB, empty)
[/LIST]
It will be organized according to the information above, like this:
[LIST=1]
[*]/hda1 (c:, NTFS, Windows XP)
[*]/hda5 (swap, -don't know which file system must be used, probably ext3-, Linux)
[*]/hda6 (/boot, ext3, Linux)
[*]/hda7 (/, root, ext3, Linux)
[*]/hda8 (/home, ext3, Linux)
[*]/hda9 (can be FAT32, to exchange data between 2 OSs)
[/LIST]
/hda5-hda9 will be created by repartitioning D: and E:.
Is the last information correct?
[/LIST]

Thank you very much in advance.

---

### Post by adwait on 2006-12-03
1) nope
2)dunno
3)No, the computer looks at the MBR, there it executes GRUB, then if you select windows, boot.ini ic called
4)
You actually don't require separate partitions for / /home /boot etc. You can just have a /swap and a / partition with the boot, home, root contained in that partition. You need a separate /home if you plan to change your distro often.

---

### Post by &amp;wP*!) on 2006-12-03
> **adwait said:**
> 
2)dunno

But you have both stuff, right? Ie. your **boot.ini** has entry for Linux, and your **grub.conf** has entry for Windows.
> 3)No, the computer looks at the MBR, there it executes GRUB, then if you select windows, boot.ini ic called
If GRUB is executes first, then why do we add entry for Linux in **boot.ini**, although it is called after GRUB?

Thank you...

---

### Post by Sef on 2006-12-03
Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").

---

