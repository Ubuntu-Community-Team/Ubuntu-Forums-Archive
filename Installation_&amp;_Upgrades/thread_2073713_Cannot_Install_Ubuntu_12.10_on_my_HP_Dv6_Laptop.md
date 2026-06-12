---
title: "Cannot Install Ubuntu 12.10 on my HP Dv6 Laptop"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by Elie-M on 2012-10-20
Well this is pissing me off.

I got a new laptop 5 days ago and I can't install the newest Ubuntu release on it.

I checked the md5 of the iso and it's matching.
I tried a USB install and a DVD install, and it just won't install.
I tried Wubi.exe to no avail.

Procedure:
- Install ubuntu
- Pick Language: english
- Press Another Continue
- I get the option: Install ubuntu inside windows, I press continue as I want to keep windows on my laptop
- the screen goes black, then ubuntu loading screen loads, and after a while I get:
Please remove installation media and close the tray(if any) then press ENTER:

I remove the cd and press enter, laptop reboots and goes directly into windows, no installation is proceeding past that.

My laptop is HP Dv6-7070ee

Any Solution? I want ubuntu.

---

### Post by albandy on 2012-10-20
Please, boot with the livecd and do the following:

open a terminal
type:
 sudo fdisk -l
post the answer.

---

### Post by oldfred on 2012-10-20
Is this a new UEFI system? fdisk may not work then.
 If fdisk does not work try this from a terminal, you can copy & paste:

```
sudo parted /dev/sda unit s print
```

If a new UEFI system did you download 64bit version as that is the only one that works with UEFI and boot liveCD in UEFI/efi mode not BIOS/AHCI/whatever mode?

---

### Post by Elie-M on 2012-10-22
> **albandy said:**
> Please, boot with the livecd and do the following:

open a terminal
type:
 sudo fdisk -l
post the answer.


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9087456e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600  1909069756   954330078+   7  HPFS/NTFS/exFAT
/dev/sda3      1909069824  1953312767    22121472    7  HPFS/NTFS/exFAT
/dev/sda4      1953312768  1953521663      104448    c  W95 FAT32 (LBA)


> Is this a new UEFI system? fdisk may not work then.
 If fdisk does not work try this from a terminal, you can copy & paste:

 	Code:
 	sudo parted /dev/sda unit s print 
If a new UEFI system did you download 64bit version as that is the  only one that works with UEFI and boot liveCD in UEFI/efi mode not  BIOS/AHCI/whatever mode?

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA TOSHIBA MK1059GS (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start        End          Size         Type     File system  Flags
 1      2048s        409599s      407552s      primary  ntfs         boot
 2      409600s      1909069756s  1908660157s  primary  ntfs
 3      1909069824s  1953312767s  44242944s    primary  ntfs
 4      1953312768s  1953521663s  208896s      primary  fat32        lba

and the image i have is a 64 bits version.

EDIT: Now This is what I get:

the installation selects "install ubuntu inside of windows"

I press continue, the screen goes black and the system restarts. Tried on another laptop, the installation went fine, so the problem is related to my laptop.

---

### Post by oldfred on 2012-10-22
Your install is in BIOS/MBR but MBR has a 4 primary partition max limit. You have to delete one primary partition and convert it to an extended partition to hold many logicals. Ubuntu works fine from logical partitions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by cyberguru on 2013-03-04
I have an HP DV6 laptop with a 750GB hard disk and I tried something similar last week but got lots of errors and failure to boot into Ubuntu 2 out of three times and issues shutting down the laptop from Ubuntu (Win 7 still worked fine). I read on another [Ubuntu] forum that it was because the logical and physical sector sizes are different on WD hard disks as seen in the line
> Sector size (logical/physical): 512 bytes / 4096 bytes from fdisk -l

---

