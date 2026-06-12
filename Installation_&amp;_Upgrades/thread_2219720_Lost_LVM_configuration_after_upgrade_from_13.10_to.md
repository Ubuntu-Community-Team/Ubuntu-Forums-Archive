---
title: "Lost LVM configuration after upgrade from 13.10 to 14.04 via live usb"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by rhills on 2014-04-25
Having done previous upgrades without any hiccups, I got slack with this one.

The computer I upgraded was running 13.10 with LVM combining multiple spindles into virtual volumes and partitions, all running nicely.

I used a 14.04 live-USB to do the upgrade.  I should have twigged when it asked me for a new user name, but I just typed in the old details again.  I guess this is not the recommended way to do an upgrade, but even googling now after the event, I can't find anything that specifically says "don't do that".

The machine upgraded OK, but now I find there is just a plain vanilla setup (LVM with root and swap_1 volumes on the primary spindle).  Of course, all my user details/customisations etc are gone. Stupidly, I'd not backed these up, though I *think* they may still be on one of the other spindles as I'm pretty sure I'd created a separate home partition on its own logical volume.

Is it possible that my old LVM stuff may be recoverable?  If so, where should I start looking?

TIA

---

### Post by rhills on 2014-04-27
OK, I've been working on this but still not sure what to do next.

What I had running on this computer previously (Ubuntu 13.10) was an LVM setup with sda (an SSD) containing boot and OS partitions, sdb and sdc (standard HDDs) containing mirrored LVM partitions.  What I can see now on sda is:
```
ubuntu@ubuntu:~$ sudo sgdisk -p /dev/sda

***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sda: 250069680 sectors, 119.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): A9582DCB-056A-4D0C-8367-FCF777652C2E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 250069646
Partitions will be aligned on 2048-sector boundaries
Total free space is 4717 sectors (2.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          499711   243.0 MiB   8300  Linux filesystem
   5          501760       250068991   119.0 GiB   8E00  Linux LVM
```
I'm guessing that somehow the upgrade process from the live USB simply blatted my previous setup and replaced it with a virginal Ubuntu 14.04 install.  I'm also guessing my old LVM setup for this spindle has been completely blatted.

My mirrored spindles show, for sdb:
```
ubuntu@ubuntu:~$ sudo sgdisk --info=1 /dev/sdb
Caution! After loading partitions, the CRC doesn't check out!
Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 6239ED61-689B-4959-9970-3DE32178ED1A
First sector: 2048 (at 1024.0 KiB)
Last sector: 1953523711 (at 931.5 GiB)
Partition size: 1953521664 sectors (931.5 GiB)
Attribute flags: 0000000000000000
Partition name: 'raid_d1'
```
and for sdc:
```
ubuntu@ubuntu:~$ sudo sgdisk --info=1 /dev/sdc
Caution! After loading partitions, the CRC doesn't check out!
Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 953B7DA4-01D7-49E3-970E-278F50C0B577
First sector: 2048 (at 1024.0 KiB)
Last sector: 1953523711 (at 931.5 GiB)
Partition size: 1953521664 sectors (931.5 GiB)
Attribute flags: 0000000000000000
Partition name: 'raid_d2'
```
So, I'm hoping that my raid partitions are still intact and possibly recoverable?  These contain data and home partitions so I'm hoping I can get these back.

My question is, how can I make these two LVM raid partitions visible to my "new" virginal Ubuntu 14.04 on sda?  Also, do I need to worry about the CRC mismatch errors at this point?

Hope someone can help!

Rob Hills
Waikiki, Western Australia

---

### Post by oldfred on 2014-04-28
I thought one of the disadvantages of LVM is that if one drive fails you lose all data, as it is over multiple drives. Or that really good backups are a requirement.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)

---

