---
title: "Help - Reformatting Drive to NTFS to Install Windows"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by Skasucks93 on 2011-09-09
I'm  trying to reformat everything and use my Windows 7 recovery DVD, but can't make the drive NTFS. I don't want to dual boot. 

I tried using gparted but the option for deleting a partition is greyed out, and the Windows DVD can't format because the drive isn't NTFS. 

Can someone help?

---

### Post by recluce on 2011-09-09
> **Skasucks93 said:**
> I'm  trying to reformat everything and use my Windows 7 recovery DVD, but can't make the drive NTFS. I don't want to dual boot. 

I tried using gparted but the option for deleting a partition is greyed out, and the Windows DVD can't format because the drive isn't NTFS. 

Can someone help?

Your partition is probably mounted. GParted cannot work on a mounted partition. As to Windows 7, it should be able to repartition the drive - but nowadays, many recovery CDs/DVDs are plain junk.

---

### Post by YesWeCan on 2011-09-09
One subtle issue is that the live CD Ubuntu activates the swap partition on the HD. So you need to deactivate it before you can delete the swap partition:
[COLOR="DarkSlateBlue"]sudo swapoff -a[/COLOR]

Use GParted "Device" menu to create a new partition table. Choose MBR (if the disk size is 2TB or less). This will erase the disk contents. Windows will see it as a new disk.

---

