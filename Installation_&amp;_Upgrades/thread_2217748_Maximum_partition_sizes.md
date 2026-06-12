---
title: "Maximum partition sizes"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by stormthirst on 2014-04-18
I'm planning on buying a 3TB drive for my new media/home server (with a view to adding additional drives later). I noted you can't install Windows on a 3TB drive - maximum 2TB partition apparently (not tried it, but read about it).

Is there a limit to the initial boot partition?

Would it be better to create (say) a 50GB partition for / and then partition the rest for /home?

Then use LVM to expand the space when I add more drives?

---

### Post by Luke M on 2014-04-18
> **stormthirst said:**
> I'm planning on buying a 3TB drive for my new media/home server (with a view to adding additional drives later). I noted you can't install Windows on a 3TB drive - maximum 2TB partition apparently (not tried it, but read about it).


You can, but only if you have EFI.

grub2 (which ubuntu uses) supports >2TB drives with either classic BIOS or EFI.

It's safest to place the bios_grub (1MB partition for grub) and /boot partitions within the first 2TB, because that way, it will work even if your BIOS doesn't support >2TB drives.

---

### Post by oldfred on 2014-04-18
You have to use gpt patitioning.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

    
Do not use Windows to partition a large drive. Some users have posted with issues.
Better to use gparted or gdisk.

 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

I do not have large drive, but now use gpt for all new drives & even larger flash drives that I format with more than one partition.

  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

With LVM you also have to have additional space for good backups. If any drive fails, you lose all data on a LVM spanning more than one drive.
      
 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

