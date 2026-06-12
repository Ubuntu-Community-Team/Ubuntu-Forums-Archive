---
title: "Windows and Partitioning"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by titus on 2005-04-10
Hi, i have two hard drives in my system (2x200gb). Here's how i partitioned prior ot installing ubuntu :

Disk 1 ------ ------- Linux , 131gb, /dev/sda1     /        type 83
                |
                 ------- Windows, 50gb, /dev/sda2   /win   type b (FAT32)
                |
                -------- Swap, 2gb, /dev/sda3          *swap type 82

Disk 2 -------------- Linux , 200gb, /dev/sdb1     /home type 83

My plan was to install windows if required, and reinstall grub or lilo.

However, windows won't see the partition i left for it when booting from a winxp install cd. It does see the type 83 linux partitions (listed as unknown). I've tried formatting the partition using 'sudo mkfs -t vfat /dev/sda2', but windows still can't see the partition.

Anyone know what i should do?

---

### Post by soul_rebel on 2005-04-10
This is a windows support question. It has difficulties in installing in partitions other than the first, it does not like other os. I suggest to take the cd and throw where it deserves: out of the window  :-D

---

### Post by PhilD on 2005-04-10
[QUOTE=titus]Hi, i have two hard drives in my system (2x200gb). Here's how i partitioned prior ot installing ubuntu :

Disk 1 ------ ------- Linux , 131gb, /dev/sda1     /        type 83
                |
                 ------- Windows, 50gb, /dev/sda2   /win   type b (FAT32)
                |
                -------- Swap, 2gb, /dev/sda3          *swap type 82

Disk 2 -------------- Linux , 200gb, /dev/sdb1     /home type 83

My plan was to install windows if required, and reinstall grub or lilo.

However, windows won't see the partition i left for it when booting from a winxp install cd. It does see the type 83 linux partitions (listed as unknown). I've tried formatting the partition using 'sudo mkfs -t vfat /dev/sda2', but windows still can't see the partition.

Anyone know what i should do?[/QUOTE]
 It is usually recommended that you install Windows first, then Linux, because Windows has a nasty habit of assuming it can overwrite the MBR, among other things. Other than starting over I don't know how to fix your current problem. Only thing I can think of is that you must install the Windows boot partition into a primary partition, not a logical one.

---

### Post by titus on 2005-04-10
lol, i agree soul, but i've got to get my eve fix  :)

yeah, i know about the whole windows first thing, but was hoping it wouldn't be too useless if i did it this way.

Oh well, how is it possible people can make a better product, and for free! amazing.

:)

so basically i've trashed / and started again. i'm writing this from windows, but i'll put ubuntu back later. At least my /home is on a different drive. I'm glad i setup this way.

Regards,

Titus.

---

