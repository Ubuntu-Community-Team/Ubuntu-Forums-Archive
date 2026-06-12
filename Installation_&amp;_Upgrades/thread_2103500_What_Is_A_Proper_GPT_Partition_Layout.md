---
title: "What Is A Proper GPT Partition Layout?"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by Kirk Schnable on 2013-01-10
**Background Information**
Over the past few days, I have been troubleshooting an issue with GRUB updates.  After spending two days staying after work hours until midnight and then 9PM last night, I've come up with a workaround for my difficulties, described in the threads below.

Here are my other threads which were related to this issue, if anyone wants to see them:
[http://ubuntuforums.org/showthread.php?p=12448235](http://ubuntuforums.org/showthread.php?p=12448235)
[http://ubuntuforums.org/showthread.php?p=12447070](http://ubuntuforums.org/showthread.php?p=12447070)

**The Original Problem**
```
root@hostname:~# grub-install --boot-directory=/boot /dev/sda/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
```
(Anyone interested in a workaround, see my other two threads).

**My Evolved Question**
As my understanding of the issue progressed, my question evolved, resulting in my ultimate decision to make two, now three different threads.

Presently, this is my partition layout on a computer which gets this error message.
```
root@hostname:~# parted /dev/sda print
Model: ATA ST9250315AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name     Flags
 1      17.4kB  248GB  248GB   ext4            primary
 2      248GB   250GB  2000MB  linux-swap(v1)  primary
```

I have come to realize that this is not a proper layout for a GPT partitioning scheme, and that's why GRUB is giving me error messages.

My difficulty with this, is the Internet seems to have a few conflicting ideas about how to do a proper GPT partition layout.

Depending on what I'm reading, there should be 2 partitions for EFI System, or 1 partition, it should be 50MB, or it shouldn't be more than 2MB... etc.  None of this has ever really mattered to me before, I've always done two partitions, an ext4 and a swap.  (or 3 with an extra for /home).

I would just appreciate a clear-cut response on what partitions I need.  I am trying to go with a partition layout which is fully compatible with GRUB, and will prevent this error message from happening in the future.

If there is any standard partition layout which will not be compatible with the way that 8 year old computers boot, I would like to avoid that one, and go with a more compatible standard.

Thanks!
Kirk

---

### Post by Cheesemill on 2013-01-10
As well as the usual partitions (root, swap, home) if you want to install GRUB on a GPT partitioned disk on a machine that boots using BIOS (not the newer UEFI) you also need an extra partition (the BIOS boot partition).

This isn't needed on msdos partitioned disks because there is room to embed the bootloader in the MBR. Because of the difference in partitioning schemes this space isn't available on GPT partitioned disks so you need to create a separate partition for this purpose.

[http://www.gnu.org/software/grub/manual/html_node/BIOS-installation.html#BIOS-installation](http://www.gnu.org/software/grub/manual/html_node/BIOS-installation.html#BIOS-installation)

I use this method on my machine with no issues, if you look at my partition layout below you can see I have a 2MiB BIOS boot partition.

```
root@arch:~# gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 125045424 sectors, 59.6 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): B0BC1FC5-D029-4693-A2D3-0DB8A98FB9D4
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 125045390
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            6143   2.0 MiB     EF02  grub
   2            6144        52434943   25.0 GiB    8300  root
   3        52434944       125045390   34.6 GiB    8300  home
``````
root@arch:~# parted /dev/sda print
Model: ATA OCZ-PETROL (scsi)
Disk /dev/sda: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3146kB  2097kB               grub  bios_grub
 2      3146kB  26.8GB  26.8GB  ext4         root
 3      26.8GB  64.0GB  37.2GB  ext4         home
```

---

### Post by darkod on 2013-01-10
First, don't use UEFI boot unless you areally have no other option. In many places on the internet EFI system partition is mentioned together with gpt BUT ONLY if you dual boot. This is because windows has limitation and it can work on gpt only with UEFI boot.

For a linux only system, you don't care about that. Linux can work on both msdos and gpt with the older style legacy boot (non-UEFI).

So, the first thing to do on a new disk you want to use as gpt, is creating the small 1MiB partition with the bios_grub flag right after you create the blank gpt table. Lets assume you got a new disk, and there is no data on it (otherwise writing a new table will DESTROY all data on it of course). Here is what I do:
```
sudo parted /dev/sda
mklabel gpt
unit MiB
mkpart GRUB 1 2
set 1 bios_grub on
quit
```

Those commands will:
Create new empty gpt table.
Change the parted unit to MiB (for easy creation of 1MiB partition).
Create partition with label GRUB from 1st to 2nd MiB (size exactly 1MiB).
Since this is the first partition it will have the number #1, so, set the bios_grub flag to 'on' on partition #1.

That's it.

You are getting this error since gpt disks have smaller MBR than msdos disks, and grub2 doesn't fit on the MBR like with msdos disks. So it needs little bit of space, even 1MiB is enough to store part of its files. You still install it to the MBR with grub-install /dev/sda, not to /dev/sda1. It will use this space automatically since the bios_grub flag tells it where it is.

Also this small partition has to be WITHOUT any filesystem, that's why it's easier to create it with parted since the mkpart creates only the partition, not a filesystem on it.

Specifically in your case, your first partition starts on only 17kB which is rather low. The general standard these days for proper partition alignment is to leave 1MiB in front of the first partition. In sectors that would be 2048 sectors of 512B each.

---

### Post by oldfred on 2013-01-10
It depends on whether booting with UEFI or BIOS. I boot with BIOS, but was buying a new system which would be UEFI, so my new SSD has both an efi partition and a bios_grub. But you only need one or the other. 

My own installs now  are usually to a 25GB / (root) including /home inside / , but all data in other partitions both NTFS & Linux formatted.

```
Disk /dev/sdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdd1                   1   117,231,407   117,231,407  ee GPT

GUID Partition Table detected.
Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1           2,048       616,447       614,400 EFI System partition
/dev/sdd2         616,448       618,495         2,048 BIOS Boot partition
/dev/sdd3         618,496    58,925,055    58,306,560 Data partition (Windows/Linux)
/dev/sdd4      58,925,056   117,229,743    58,304,688 Data partition (Windows/Linux)

```

Then how you partition drive for Ubuntu is totally up to you. Each of us has different uses and that often changes requirements. Even my own optimal partitioning scheme a year or two later is not so good as I have changed what I am doing. 
But my suggestions:

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
    
Windows only boots from gpt with UEFI, so it needs efi partition not bios_grub. But Windows creates a partition like bios_grub that it calls MSR or Microsoft reserved. It is like bios_grub in that it is not formatted and seems to be for some of the serial number or DRM info that was between MBR and first partition (or just like grub's core.img). Windows then usually have a recovery partition (repair) and Vendor recovery (total restore) partitions.
       Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

---

