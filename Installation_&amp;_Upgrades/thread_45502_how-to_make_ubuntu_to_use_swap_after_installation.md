---
title: "how-to make ubuntu to use swap after installation?"
date: 2005-06-30
forum: Installation &amp; Upgrades
---

### Post by jayson on 2005-06-30
hi!
i got a little problem with swap using.

here is my situation:
firstly i deleted all partitions in my HDD and created NTFS for windows xp what i installed after this. then i started to install ubuntu and becoruse i wanted to create FAT32 partition after Ubuntu installation i didn't want to use all disc free space and so i partition it manually, i did EXT3 logical partition and ubuntu installed on it. BUT, it didn't create SWAP, so later in win xp @ partition manager i created manually SWAP partition. but now ubuntu isn't using any swap space becourse it didn't create it on the beginning.
so here is my question: how i can make ubuntu to use swap space now?

thank you...

---

### Post by jasmuz on 2005-06-30
[QUOTE=jayson]hi!
i got a little problem with swap using.

here is my situation:
firstly i deleted all partitions in my HDD and created NTFS for windows xp what i installed after this. then i started to install ubuntu and becoruse i wanted to create FAT32 partition after Ubuntu installation i didn't want to use all disc free space and so i partition it manually, i did EXT3 logical partition and ubuntu installed on it. BUT, it didn't create SWAP, so later in win xp @ partition manager i created manually SWAP partition. but now ubuntu isn't using any swap space becourse it didn't create it on the beginning.
so here is my question: how i can make ubuntu to use swap space now?

thank you...[/QUOTE]
 To activate it while you run, go to the terminal and type sudo swapon /dev/hdx (X is replace with your own).

Then to make the swap file permanent, type in the command line : sudo gedit /etc/fstab

There add your swap partition like this:

/dev/hdx       none            swap    sw              0       0

---

### Post by mingus on 2005-06-30
*in win xp @ partition manager i created manually SWAP partition*

umm . . . I don't think so.  W$ Disk Manager cannot create Linux partitions.  Please  explain.

How did you create the NTFS partition?  The FAT32 partition?  The Ubuntu partition?

In Ubuntu do:
$sudo fdisk -l

and post back results here.

---

### Post by jayson on 2005-06-30
thank you jasmuz, it worked fine!

to: mingus
sorry, i ment Powerquest Partition Magic, not manager.

---

### Post by mingus on 2005-06-30
[QUOTE=jayson]
to: mingus
sorry, i ment Powerquest Partition Magic, not manager.[/QUOTE]

ah yes, now that makes sense

---

