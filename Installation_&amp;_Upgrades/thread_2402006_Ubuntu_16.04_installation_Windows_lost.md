---
title: "Ubuntu 16.04 installation Windows lost"
date: 2018-09-25
forum: Installation &amp; Upgrades
---

### Post by rensisam on 2018-09-25
I was trying to install Ubuntu 16.04 into a system where Windows 7 was already installed.

Meanwhile, I lost the Windows 7 boot.

So I am not able to boot into it.
I followed the advice  in [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair), installed boot-repair from Live USB .and got the URL [http://paste.ubuntu.com/p/nVKKymyP3M/](http://paste.ubuntu.com/p/nVKKymyP3M/)

But I am still not able to boot to Windows.

Kindly look into my specific problem and help.

Thanking you
Rensi

---

### Post by yancek on 2018-09-25
Your system is Legacy/MBR which means you are only allowed 4 primary partitions.  You already have 4 primary partitions used for windows so you cannot install another OS without changing that.  Have you used/tested Ubuntu to see if it works from the "Try Ubuntu" option on the usb?   If not, I would suggest you do that before trying to install again.  What you would need to do with your current setup is to delete one of your windows partitions to make room for Ubuntu.  Don't recommend that.

Another option in addition to testing the Live USB is to install VirtualBox or other virtual software in windows and use Ubuntu that way.

Your drive is using Dynamic Disks for three of your windows partitions indicated by the SFS under the drive info.  You won't be able to install Linux on that machine without changing this and I don't know how you would do that or if it is possible without data loss.

Options other than Virtual Software, install to an external usb drive or a flash drive.

---

### Post by oldfred on 2018-09-25
Be sure to have good backups, which you should have anyway if running Windows.

[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[URL="http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html"]http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html

[/URL]
 Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm) 
   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005) 

[URL="http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html"]
[/URL]

---

### Post by rensisam on 2018-09-25
I have logged in using Live USB.
I can see my Windows file insides(C Drive). Also I can see the other Window partitions.

root@ubuntu:/home/ubuntu# os-prober

/dev/sda1:Windows 7 (loader):Windows:chain

root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/loop0: 1.5 GiB, 1587904512 bytes, 3101376 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes


I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disklabel type: dos

Disk identifier: 0xabcc1cd3


Device     Boot     Start        End    Sectors   Size Id Type

/dev/sda1              63       2047       1985 992.5K 42 SFS

/dev/sda2  *         2048     206847     204800   100M 42 SFS

/dev/sda3          206848  524290047  524083200 249.9G 42 SFS

/dev/sda4       524290048 1953523119 1429233072 681.5G  7 HPFS/NTFS/exFAT


Partition 1 does not start on physical sector boundary.





Disk /dev/sdb: 14.7 GiB, 15724707840 bytes, 30712320 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disklabel type: dos

Disk identifier: 0x001e9453


Device     Boot Start      End  Sectors  Size Id Type

/dev/sdb1  *     2048 30712319 30710272 14.7G  c W95 FAT32 (LBA)

---

### Post by oldfred on 2018-09-26
All that info was in Boot-Repair's Summary Report.

Issue is SFS which in Linux means you have Windows dynamic partitions.

/dev/sda1              63       2047       1985 992.5K 42 [COLOR=#ff0000]SFS[/COLOR]
/dev/sda2  *         2048     206847     204800   100M 42 [COLOR=#ff0000]SFS[/COLOR]
/dev/sda3          206848  524290047  524083200 249.9G 42 [COLOR=#ff0000]SFS[/COLOR]

---

