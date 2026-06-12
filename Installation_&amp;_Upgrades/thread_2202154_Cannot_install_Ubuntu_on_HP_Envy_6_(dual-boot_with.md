---
title: "Cannot install Ubuntu on HP Envy 6 (dual-boot with Win7)"
date: 2014-01-27
forum: Installation &amp; Upgrades
---

### Post by fifoo on 2014-01-27
All,

I've been trying to install Ubuntu 13.10 on an HP Envy 6 with Win7 pre-installed without success. I've also tried Ubuntu 12.04, same behaviour.

I'm installing from a USB key. I can boot from the USB Key and start the installation process. The problem is when I come to the partition page (GRUB install page?) when I should be able to choose the partition where I want to install Ubuntu : here nothing is shown. "/dev/sda" is shown in the dropdown menu at the bottom but that's all and I cannot do anything.

I can launch Gparted in the Live session and there, all partitions are seen, no problem: I've created a 150GB free partition under Windows and I could format it in ext4 in Gparted.

I've read a lot of things about EFI and secure boot, etc... however this does not seem to apply to my PC (no such options in BIOS). So I'm a bit stuck....

Thanks in advance for your help!

L.

---

### Post by oldfred on 2014-01-27
If using Something Else and do not have partitions you have to use + to add or if you created in advance with gparted, then use Change button to create / partition at the minimum.

Post this from your live installer's terminal.

sudo parted -l

---

### Post by fifoo on 2014-01-28
Thanks for your reply.

I do not have the first screen as you posted (Installation Type). I directly get to the 2nd screen which is empty (as described in my first post). Also weird, is the fact that the disk name is not displayed next to "/dev/sda".

It looks like Ubuntu does not detect that Windows is installed on my laptop ?

I'll run the command as you asked when I get home.

---

### Post by oldfred on 2014-01-28
It may be one of these type issues, hopefully parted info will narrow it down.

 Boot Issues from live Installer not showing partitions
Do you have Windows hibernated?  Or Windows 8 fastboot still on
Does NTFS need chkdsk? Even if it boots ok?
Was drive every part of RAID or RAID set in BIOS? or Intel SRT which uses RAID
SFS, Windows dynamic partitions or LDM on gpt drives
 backup GPT table is not at the end of the disk
Left over gpt data Windows leaves backup gpt data when converting to MBR.
Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by fifoo on 2014-01-28
Here is the result of 'sudo parted -l'   

[FONT=courier new]ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   315GB  315GB   primary  ntfs
 4      315GB   476GB  161GB   primary  ext4
 3      476GB   500GB  23.8GB  primary  ntfs


Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8589MB  8588MB  primary
[/FONT]

---

### Post by fifoo on 2014-01-28
And this is how it looks on the Windows front (image attached).

---

### Post by fifoo on 2014-01-28
> Do you have Windows hibernated?  Or Windows 8 fastboot still on
No / I use Windows 7.

> Does NTFS need chkdsk? Even if it boots ok?
I did a chkdsk, all was fine.

> Was drive every part of RAID or RAID set in BIOS? or Intel SRT which uses RAID
No

>  SFS, Windows dynamic partitions or LDM on gpt drives
Sorry, I'm lost

 > backup GPT table is not at the end of the disk
> Left over gpt data Windows leaves backup gpt data when converting to MBR.
How could I check that?

Thanks again for your help.

---

### Post by oldfred on 2014-01-28
It is normal that Windows does not correctly see a Linux formatted partition.
Partitions look normal in parted list.

I might delete ext4 partition with gparted and create two logical partitions so you can have both / and swap. Or delete and leave unallocated and do an auto install. But do not use any auto install that does not offer side by side install with Windows. If the installer does not see Windows it will overwrite it.

---

### Post by fifoo on 2014-01-30
Unfortunately, I tried what you suggested without success. I deleted the partition and create 2 new partitions in Gparted. But still the same behaviour in the installer: when displaying the partition window, no partition is displayed. My feeling is that is does see the partitions (Gparted does so there is no reason for the installer not to), but it cannot see Windows somehow (as I do not have the "install alongside Windows" window). Maybe it is the recovery partition that is confusing the installer...

I'm thinking about wiping the disk and installing Ubuntu then Windows.... But if you still have an idea, I'll take it! Thanks again.

---

### Post by fantab on 2014-01-30
> **fifoo said:**
> Unfortunately, I tried what you suggested without success. **I deleted the partition and create 2 new partitions in Gparted**. 

```
[FONT=courier new]$ sudo parted -l
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   315GB  315GB   primary  ntfs
 4      315GB   476GB  161GB   primary  ext4
 3      476GB   500GB  23.8GB  primary  ntfs[/FONT]
```

Did you create an EXTENDED Partition? Or did you just deleted and created two new partitions instead?

Post the output of:
```
sudo fdisk -l
sudo parted -l
```

---

### Post by oldfred on 2014-01-30
Usually best to have Windows installed first.

Normally the parted info would show any gpt or RAID type issues. Repost as per fantab's request.

What mode is BIOS settings for drives in. Is it in AHCI not IDE nor RAID?

---

### Post by mastablasta on 2014-01-30
> **fifoo said:**
> My feeling is that is does see the partitions (Gparted does so there is no reason for the installer not to), but it cannot see Windows somehow (as I do not have the "install alongside Windows" window). .

you get the "install alongside Windows" if you leave ***unformated disk space***. so just delete partition and try if this option show up as available. 
if you preformat the parittions then you need to go manual.

make sure you have only 3 primary partitions occupied before doing the install procedure.

---

### Post by fifoo on 2014-01-30
Yes, I created an extended partition.

Here it is:
```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  210MB  209MB   primary   ntfs         boot
 2      210MB   315GB  315GB   primary   ntfs
 4      315GB   476GB  161GB   extended
 5      315GB   462GB  147GB   logical   ext2
 6      462GB   476GB  14.3GB  logical   ext2
 3      476GB   500GB  23.8GB  primary   ntfs


Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8589MB  8588MB  primary


```
```

ubuntu@ubuntu:/home$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x8dfc4234

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   615716863   307653632    7  HPFS/NTFS/exFAT
/dev/sda3       930289664   976762879    23236608    7  HPFS/NTFS/exFAT
/dev/sda4       615716864   930289663   157286400    5  Extended
/dev/sda5       615718912   902438911   143360000   83  Linux
/dev/sda6       902440960   930289663    13924352   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24784b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    16775167     8386560   84  OS/2 hidden C: drive


```

---

### Post by fifoo on 2014-01-30
Attached is the printscreen of the empty window. And if I click '+', I've got a crash of ubiquity...

---

### Post by oldfred on 2014-01-30
Is this an Ultrabook?
That uses RAID as part of the Intel SRT.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

### Post by fifoo on 2014-02-01
Yes this is an Ultrabook. I've just discovered what it was all about (see below).

I finally decided to wipe the disk off to install Ubuntu on a clean disk. Unfortunately, I still add the same behaviour: I could delete and create as many partitions as I wanted in Gparted, but still impossible to install Ubuntu until... I used the "Write partition table" menu in Gparted. Finally, the Ubuntu installation could succeed.

About Ultrabook now. You're right about RAID. When I rebooted, some special Intel BIOS page asked me if I wanted to perform some setup. When I entered the menu, it was indeed question of RAID: correct me if I'm wrong, but it looks like the main disk and the 32GB SDD are mounted in a RAID array. What I did was to remove the SSD from the RAID array.

Naively, I thought I could use the SSD to install Windows on it but I could not (Windows can format it, but cannot do whatever it needs to during installation). From googling around, I'm not sure it is possible to do that as the disk is used for caching internally by the system and cannot be used as a normal disk. I haven't investigated further so again, correct me if I'm wrong.

Finally I will install Windows in VirtualBox, that suits my needs.

Thanks for your help.

---

### Post by oldfred on 2014-02-01
Windows requires fast booting. So vendors add a small SSD to be just for cache to speed booting.

Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

      
 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by fifoo on 2014-02-04
Thanks for the very precise info. I'm sure it would have worked for me. Marking at SOLVED.

---

