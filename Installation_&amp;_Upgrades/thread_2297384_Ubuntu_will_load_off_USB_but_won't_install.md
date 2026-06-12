---
title: "Ubuntu will load off USB but won't install"
date: 2015-10-03
forum: Installation &amp; Upgrades
---

### Post by elsie2 on 2015-10-03
I am not very computer literate so you will really have to ELI5 (or maybe younger- Kid's are crazy clever these days!) 
My windows system suddenly died last week so my lovely brother put Ubuntu on a USB for me. I can load it from the USB and it works like a dream. The only problem is that I can't copy any files from my hard drive onto my external hard drive. 
I have also tried to install Ubuntu from the USB but it gets to the 'preparing to install' page and when I click Continue the loading disc appears and then just spins for eternity. 3 dots of the 7 at the bottom are red and it never moves past this stage.

I've had a look through the forum but haven't found any similar issues. I'm sorry if I've missed a solution somewhere. If I have please could someone send me a link.

Thanks in advance x

---

### Post by v3.xx on 2015-10-03
There are different versions of Ubuntu and different flavours, please tell us which one you have.

This can be displayed in terminal by pressing Ctrl + Alt + T and entering:

```
lsb_release -a
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

Don't worry about your skill level, feel free to ask questions :)

---

### Post by elsie2 on 2015-10-03
Thank you :) 
It says- Ubuntu 14.04.3 LTS
is this what you mean?

---

### Post by yancek on 2015-10-03
So you have a Live CD of Ubuntu on a flash drive.  To copy to a partition on an external drive you would need to have ownership and permissions.  If it won't install, it might be because there is no unallocated space on the drive.  When you boot Ubuntu, open a terminal and run the two separate commands below and post the output here:

```
sudo fdisk -l
sudo parted -l
df -h
```

Those are lower case Letter L in the first two commands.  This will give useful information on the drives/partitions

---

### Post by elsie2 on 2015-10-03
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x290908ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976771071   488384512    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 32.0 GB, 32015679488 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    62530623    31265296    c  W95 FAT32 (LBA)

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002b79d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   976773167   488385560    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo parted -l
^CModel: ATA WDC WD5000BEVT-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs         boot


Model: SanDisk Cruzer Force (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  32.0GB  32.0GB  primary  fat32        boot, lba


Model: WD 5000AAD External (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs

---

### Post by yancek on 2015-10-03
If the 32GB drive is your flash drive on which you currently have Ubuntu as a Live CD, then both your other (500GB) drives have only one partition on them using up the entire drive.  You would need to resize (shrink) that partition on whichever drive you want to install to which will create unallocated space on which you could install Ubuntu.  It is better if you can do this from windows with the Disk Management tool.  If you can't boot your windows system, you might be able to attache the drive to another computer and use the software on it to shrink one of the partitions.  I don't use windows so...?  You could also do it with GParted, the partition manager on the Ubuntu flash drive you are using which usually works but isn't recommended except as a last resort.  When you start the installer, you should select the Something Else option which will give you more control over what you want to do.

It would also be useful if you could post the version of windows you have as that will make a difference if it is 8 or newer.

You should be able to copy folders/files from one drive to another with the flash drive.  Not knowing what the permissions are, it's hard to suggest anything.  Ubuntu usually makes external hard drive partitions available under the /media directory so you could run the command:  ls -l /media/ubuntu/ (Lower Case L in the command) to see the output and post it here with both drives attached.  Probably owned by the root user.

---

