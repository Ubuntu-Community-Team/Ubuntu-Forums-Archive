---
title: "Problem removing ubuntu."
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by NathanBrazil on 2007-07-15
Hello everyone. Well I've tried ubuntu for two weeks and have come to the conclusion that it's not right for me. I've tried booting windows through the cd drive but when I continue with the installation it doesn't recognize my hard drive. It won't even show up as an option to install windows on. Any help? :(

Thanks in advance.

---

### Post by Vajra Vrtti on 2007-07-15
Do you have dual boot (Ubuntu+Windows) or just Ubuntu?

---

### Post by NathanBrazil on 2007-07-15
Just ubuntu.

---

### Post by Vajra Vrtti on 2007-07-15
So, the problem is that Windows won't recognize the Ubuntu's ext3 partition. At the very beginning of the Windows installation you have the option to edit you disk partitions. Delete **all** partitions (I'm assuming you don't have any data in the disk you want to preserve) and create a new NTFS partition using all available space.

> Well I've tried ubuntu for two weeks and have come to the conclusion that it's not right for me.Just curious: why not?

---

### Post by Wim Sturkenboom on 2007-07-15
I don't know why this can be the case, but you can try to boot from the Ubuntu CD.

Open a terminal and issue the following command
```

fdisk -l

```It will show all partitions. If you have one HD, they will be /dev/hdaX or /dev/sdaX.
next issue (assuming it's /dev/sdaX that you find)
```

fdisk /dev/sda

```
[LIST=1]
[*]press **p** followed by <enter> to print the partition table (not really necessary in your case as you probably want to delete all partitions)
[*]press **d** followed by <enter> to delete a partition; you are prompted for a partition number to delete; enter the number of a partition that you want to delete followed by <enter>
[*]once you have deleted them all, press **w** followed by enter to write the partition table
[/LIST]
Next you can boot from the Windows CD and it should work.

PS you need root privileges; not sure if you have them by default on the liveCD

Example (please not that in this case hdc and not sda)
```

wim@ubuntu-desktop2:~$ **sudo fdisk /dev/hdc**

The number of cylinders for this disk is set to 9733.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): **p**

Disk /dev/hdc: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1          32      257008+  82  Linux swap / Solaris
/dev/hdc2              33         780     6008310   83  Linux
/dev/hdc3             781        1528     6008310   83  Linux
/dev/hdc4            1529        9733    65906662+   5  Extended
/dev/hdc5            1529        4019    20008926   83  Linux
/dev/hdc6            4020        6510    20008926   83  Linux
/dev/hdc7            6511        9733    25888716    c  W95 FAT32 (LBA)

Command (m for help): **d**
Partition number (1-7): 7
Command (m for help): **d**
Partition number (1-6): 6
...
...
Command (m for help): **w**
wim@ubuntu-desktop2:~$

```

Although it's not my business, just curious why Ubuntu is not for you.

---

### Post by NathanBrazil on 2007-07-15
> **Vajra Vrtti said:**
> So, the problem is that Windows won't recognize the Ubuntu's ext3 partition. At the very beginning of the Windows installation you have the option to edit you disk partitions. Delete **all** partitions (I'm assuming you don't have any data in the disk you want to preserve) and create a new NTFS partition using all available space.

Just curious: why not?

I've got alot of windows based programs and games, and honestly I feel I don't know enough about computers to use ubuntu efficiently.

---

