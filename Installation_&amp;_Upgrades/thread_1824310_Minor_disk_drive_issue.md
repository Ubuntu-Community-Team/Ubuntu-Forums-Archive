---
title: "Minor disk drive issue"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by MrGrado on 2011-08-13
I have two hard drives in my computer and one has ubuntu 11.04 installed. The other drive doesn't have anything on it that is required as far as I know.

I want to take the hard disk out that isn't being used but when I do ubuntu will not boot up.

---

### Post by lmarmisa on 2011-08-13
I think that your problem will be solved after your reinstall the grub loader in the MBR of your Ubuntu hard drive. Maybe you have to take a look to the BIOS menu in order to define your boot disk too.

First of all, post the result of this command:

```

sudo fdisk -l

```

---

### Post by MrGrado on 2011-08-13
thanks for the fast reply. 

```
Disk /dev/sda: 203.9 GB, 203927027200 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17847   143355996    7  HPFS/NTFS
/dev/sda2           17848       24792    55785712+   7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe92cb5b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

Disk /dev/dm-0: 203.9 GB, 203927026176 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1       17847   143355996    7  HPFS/NTFS
/dev/dm-0p2           17848       24792    55785712+   7  HPFS/NTFS

Disk /dev/dm-1: 146.8 GB, 146796539904 bytes
255 heads, 63 sectors/track, 17846 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-2: 57.1 GB, 57124569600 bytes
255 heads, 63 sectors/track, 6945 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-2p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-2p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-2p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d2a83

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       12161    97683201    c  W95 FAT32 (LBA)

```

---

### Post by lmarmisa on 2011-08-13
Hmmm. The problem is not so simple as I supposed. Are you using some RAID solution?. How many hard drives have you connected?.

---

### Post by MrGrado on 2011-08-13
There are 3 hard drives at the moment. There is a 2TB drive, a 200GB drive, and a 100GB USB HHD.

Ubuntu is on the 2TB drive, Kubuntu is on the 100GB USB drive in live CD type form and there is no other operating systems.

There is no raid array.

---

### Post by lmarmisa on 2011-08-13
And what about the devices /dev/dm-x?. What are theses devices?. What hard drive do you wish to remove?.

---

### Post by lmarmisa on 2011-08-13
Your 2 TB is using GPT and fdisk does not support this option.

Try to post the result of this other command:

```

sudo parted -l

```

---

### Post by MrGrado on 2011-08-13
I suppose those dev/dm-x devices are part of the 200GB drive, which is the drive I want to remove.

---

### Post by MrGrado on 2011-08-13
```
mrgrado@GradoBox:~$ sudo parted -l
[sudo] password for mrgrado: 
Model: ATA Maxtor 6L200M0 (scsi)
Disk /dev/sda: 204GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  147GB  147GB   primary  ntfs         boot
 2      147GB   204GB  57.1GB  primary  ntfs


Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  1018kB  1000kB                        bios_grub
 2      1018kB  1998GB  1998GB  ext4
 3      1998GB  2000GB  2147MB  linux-swap(v1)


Model: ST910082 4A (scsi)
Disk /dev/sdc: 100GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  100GB  100GB  primary  fat32        boot, lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/nvidia_egfaaafb: 204GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  147GB  147GB   primary  ntfs         boot
 2      147GB   204GB  57.1GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

mrgrado@GradoBox:~$ ^C
mrgrado@GradoBox:~$ 

```

---

### Post by lmarmisa on 2011-08-13
The last command **sudo parted -l** did not show your 100 GB hard drive. I suppose that this disk is still there but the command was not able to show it.

I am not sure that the GRUB loader can be easily installed in your 2 TB hard drive taking into account that this drive is using GPT and not MBR.

So, I recommend to install GRUB in the MBR of your 100 GB hard drive.

Please, follow this procedure. Boot into Ubuntu and type the command:

```

sudo fdisk -l

```

Check if the 100 GB hard drive is detected as device **/dev/sdc**. If so, type this other commands:

```

sudo update-grub
sudo grub-install /dev/sdc

```

Shutdown your system.

Then enter your BIOS menu and select the 100 GB hard drive as boot device. I think that you will be able to boot your system from this 100 GB device. If the boot is successful, remove your 200 GB hard drive. 

I hope that you will get no more problems at  startup.

Best regards,

Luis

---

### Post by srs5694 on 2011-08-13
It appears that you've got some remnants of a motherboard-based software RAID (aka "fake RAID") configuration -- that's what the /dev/dm-1, /dev/dm-2, and /dev/mapper/nvidia_egfaaafb device files represent. If that leftover data is stored on /dev/sda (which I assume is the drive you want to remove), it should go away once you remove the drive. AFAIK, this is not likely to be related to your problem; however, I'm not an expert on this type of RAID.

My suspicion is that you just need to re-install GRUB. There are several ways to do this. The way I'd do it is as follows:


[list=1]
[*]Download [Super GRUB 2 Disk](http://www.supergrubdisk.org) (note the "2") and burn a copy to CD.
[*]Physically remove /dev/sda.
[*]Boot using Super GRUB 2 Disk. It should give you several options to detect your OS. You may need to try several of these. Try them until you find one that works.
[*]Once you're booted into your regular system, type "sudo grub-install /dev/sda" in a terminal window.
[*]Remove the Super GRUB 2 Disk from the CD/DVD drive.
[*]Reboot. The computer should now boot normally from the hard disk.
[/list]


If Super GRUB 2 Disk can't detect your installation, then you may need to attempt another method of installing it to the hard disk. There are ways to do this before removing /dev/sda or by using the Ubuntu installer, but I don't have exact procedures or commands memorized. (Perhaps just "sudo grub-install /dev/sdb" would work after booting with /dev/sda installed, but I'm far from certain of this.) Somebody else may post a suggestion along these lines.

---

### Post by srs5694 on 2011-08-13
> **lmarmisa said:**
> I am not sure that the GRUB loader can be easily installed in your 2 TB hard drive taking into account that this drive is using GPT and not MBR.

It can be installed. The disk already has a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) on it -- that's what the "bios_grub" flag in the parted output indicates. Thus, GRUB 2 should detect and use the GPT partitions and the BIOS Boot Partition without problems.

---

### Post by lmarmisa on 2011-08-13
> **srs5694 said:**
> It can be installed. The disk already has a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) on it -- that's what the "bios_grub" flag in the parted output indicates. Thus, GRUB 2 should detect and use the GPT partitions and the BIOS Boot Partition without problems.

My proposal (post #10) was cautious because I thought that a bad installation of the GRUB loader in the 2 TB hard drive could damage the data structures of that device. But I think that installing the GRUB loader in the MBR of the 100 GB hard drive is a valid solution too.

What command do you propose?. Simply?

```

sudo grub-install /dev/sdb

```

---

### Post by srs5694 on 2011-08-13
GRUB 2 is GPT-aware, so there's little risk of a GRUB 2 re-installation damaging the GPT data structures. The only way that would happen would be if there were a bug, if the GPT data structures were damaged, or if there's a hardware error. These would be risks when re-installing GRUB to an MBR disk, too, and they're very minor risks. Of course, backing up your data is in order, but that's no more true of this situation than of any other.

I suggested a procedure in my earlier post (#11 in this thread).

---

### Post by YesWeCan on 2011-08-13
If you boot into Ubuntu on the 2TB as usual and run
[COLOR="Navy"]sudo grub-install /dev/sdb[/COLOR]
As has already been suggested twice. That should work.
Also run
[COLOR="Navy"]sudo apt-get install dmraid[/COLOR]
To see which disks have old Windows RAID superblocks on them
[COLOR="Navy"]sudo dmraid -s[/COLOR]
Remove from a disk using
[COLOR="navy"]sudo dmraid -Er /dev/sdx[/COLOR]  (x=a,b,c as required)

---

