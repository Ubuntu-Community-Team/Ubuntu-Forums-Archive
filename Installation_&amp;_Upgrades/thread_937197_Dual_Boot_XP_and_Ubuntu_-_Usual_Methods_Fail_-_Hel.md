---
title: "Dual Boot XP and Ubuntu - Usual Methods Fail - Help Please"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by fidgaf on 2008-10-03
A bit of a long explanation but it's needed so I don't get directed to the usual dual boot links. I have had no luck there.

I have been using Ubuntu for some time in a partition on my XP drive. Occasionally I have had to fix the MBR and re-instate the /boot/grub/menu.lst

I'm confident on how to do this on the old setup - but now I'm stuck.

**Why:**

Old System - 2 x IDE 80GB Hard Drives.
[LIST]
[*]IDE 0 = XP Pro + Ubuntu partition(s) + another partition
[*]IDE 1 = Several partitions
[/LIST]

New System - 2 x IDE 80GB hard drives + 2 x SATA 500GB Hard Drives.
[LIST]
[*]IDE 0 = Ubuntu (clean, new, whole drive install)
[*]IDE 1 = 1 x NTFS Partition
[*]SATA 2 = Windows XP Pro (Clone of old - works fine) + 2 x NTFS partitions
[*]SATA 3 = 4 x NTFS partitions
[/LIST]

I can set my system from the F2 set-up to boot either XP on the SATA 2 or Ubuntu on IDE 0 - Both work fine.


**What I Want To Do:**

I don't mind whether I have the option to boot Ubuntu in XP's startup menu or whether I use Ubuntu's /boot/grub/menu.lst

Currently I can do neither.



The best advice I found was to have this in /boot/grub/menu.lst

```

title                Windows XP Professional
root                (hd1,0)
savedefault
makeactive
chainloader        +1
map (hd0) (hd1)
map (hd1) (hd0)
```

Mapping back and forth seemed to make sense but I had no idea how Ubuntu was identifying my drives. fdisk -l was suggested and no help at all (can you see any reference to hdx ?)

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: xxxxxxxxx7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: xxxxxxxxx0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS
/dev/sdb2            9729        9729        8032+   f  W95 Ext'd (LBA)

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: xxxxxxxxx6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19465   156352581    7  HPFS/NTFS
/dev/sdc2           19466       60801   332031420    f  W95 Ext'd (LBA)
/dev/sdc5           19466       39863   163846903+   7  HPFS/NTFS
/dev/sdc6           39864       60801   168184453+   7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: xxxxxxxxxb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       15206   122142163+   7  HPFS/NTFS
/dev/sdd2           15207       60801   366241837+   f  W95 Ext'd (LBA)
/dev/sdd5           15207       30411   122134131    7  HPFS/NTFS
/dev/sdd6           30412       45616   122134131    7  HPFS/NTFS
/dev/sdd7           45617       60801   121973481    7  HPFS/NTFS

```

(I notice W95 in there but it is definitely XP and has never been soiled with Windows 95. I guess it's a legacy thing or means something else).


As I said an XP or an Ubuntu solution is fine.

I would prefer Ubuntu.

However, I'm currently using XP most so I'm booting into XP with no access to Ubuntu without a lot of fiddling about in Boot options.

Sadly, migrating work from XP to Ubuntu has stopped.

Please help. :)


Thanks in advance for your time.



PS - Ubuntu can mount all the XP partitions but not the XP O/S partition (something about RAID which is odd as it's not activated or installed on XP). If it's an easy fix, that would be fine - If not, it is a minor glitch - 99.999% of the time I need nothing from there for Ubuntu.

.

---

### Post by caljohnsmith on 2008-10-03
So can you boot into Ubuntu at all right now? 

I think your best strategy would be to set your Ubuntu HDD as the drive that boots on start up, and then we should be able to easily modify your menu.lst so you can boot Windows. The small problem is that we don't know whether Windows is on (hd1), (hd2), or (hd3) when Grub boots on start up, because the order of drives on start up is the same as the BIOS boot order, not the same as the drives are ordered in /dev when you boot into Ubuntu. So bottom line, if you can boot your Ubuntu drive and get the Grub menu fine, then add all three of these entries to your menu.lst, and one should boot Windows (assuming Windows is in the first partition):
```
title                Windows XP Professional (hd1)
root                (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader        +1

title                Windows XP Professional (hd2)
root                (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader        +1

title                Windows XP Professional (hd3)
root                (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader        +1
```
Once you figure out which works, you can just delete the others. Or if you aren't able to boot the Ubuntu drive OK right now, let me know and we can work from there. Let me know how it goes or if you need more info/details. :)

---

### Post by fidgaf on 2008-10-04
A simple but elegant solution that worked a treat. :)

Thanks caljohnsmith.

I was so near but so far.

I was always able to boot Ubuntu but needed to change the Boot order in Setup each time I wanted to switch between XP and Ubuntu.

Now I'm very happy, Ubuntu is my default boot O/S and, as they're on separate hard drives, I should be immune to Microsoft's new habit of trashing /boot/grub/menu.lst when they do updates (SP3 being the latest to do so).

Thanks again.

---

### Post by caljohnsmith on 2008-10-04
Glad that you have Windows booting fine now, fidgaf. Cheers and have fun. :)

---

