---
title: "Dual boot and lost space"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by tankmil on 2011-03-06
Hi,

I am new to this, but here it goes.
I have a machine with both Win 7 and Ubuntu installed.

A few days ago something happened to my Ubuntu and I had to reinstall it. In the process, I think (not sure) that I installed the new Ubuntu on a new partition that got taken away from Win's free space. Meanwhile, I think (again, not sure), that the old, bad install of Ubuntu is still sitting there taking up space. I see all it's kernel boots in the boot menu, when I start the machine. Some of them are identical to the new Ubuntu boot options, but they are listed below the Windows 7 boot option.

I have several, how to's:

1. How do I check if there are inaccessible partitions, taken up by the old Ubuntu Install?
2. If 1 is Yes, how can I free up this space, and give it back to Windows?

Thanks.

---

### Post by YesWeCan on 2011-03-06
Please post the output of 'sudo fdisk -l'
This will show all your disks and their partition types in crude format.

You can also use the System/Administration/Disk Utility to get a clear view of your partitions.
You can select a partition here and delete it. Be very careful not to delete any Windows ones. Windows 7 may have a small boot partition too.
Once you have freed space after the Windows partition you need to boot Windows and use its disk utility to reclaim the space.

---

### Post by tankmil on 2011-03-06
here is the output:

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x26b25fba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896   27  Unknown
/dev/sda2   *        1568        1580      104422+   7  HPFS/NTFS
/dev/sda3            1581       20359   150839740+   7  HPFS/NTFS
/dev/sda4           20359       30402    80666625    5  Extended
/dev/sda5           20359       26032    45569427+  83  Linux
/dev/sda6           29987       30402     3329024   82  Linux swap / Solaris
/dev/sda7           26032       29818    30406656   83  Linux
/dev/sda8           29818       29986     1352704   82  Linux swap / Solaris


```

---

### Post by YesWeCan on 2011-03-06
This is a laptop, right?
sda1 is probably a recovery partition for Windows.
sda2 is the small Windows boot partition
sda3 is Windows
sda5-8 are Ubuntu

Now things may get a bit tricky.
The trouble is that the disk now uses grub to boot. Grub needs files inside your newest Ubuntu partition. If it cannot find these it will fail to boot either Windows or Ubuntu.
So you must not delete the wrong Ubuntu. Also, moving the Ubuntu partition may stop grub finding the files (I am not sure about this).

There is a hard way to do this and an easy but tedious way.
The easy way is to use your Windows CD to reinstate the Windows MBR (removes grub) and then allows you to boot Windows only. Then use Windows disk manager to reclaim space and wipe Ubuntu out. Then reinstall Ubunu from scratch.

I have not done this, but I think the hard way requires you to boot from a live Ubuntu CD and use Gparted to delete, say sda7 & 8 and then move sda4 5 & 6 to the right to open space after Windows. Then mount the Ubuntu partition, sd5, and reinstall grub, then reboot into Windows and grow the Windows partition.

Or someone else may have a niftier solution.

---

### Post by YesWeCan on 2011-03-06
To reinstall grub using the live CD, assuming your ubuntu root partition is sda5, you need to:
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
then reboot off the hard drive into Ubuntu.
then sudo update-grub
to make sure Windows is still in the boot menu.

---

### Post by tankmil on 2011-03-07
Thanks,

I will try the options you mentioned.
By the way, what gives away that it is a laptop?

---

