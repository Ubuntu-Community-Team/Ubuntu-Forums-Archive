---
title: "Ubuntu 10.04 doesn't recognize HDDs during installation"
date: 2013-11-12
forum: Installation &amp; Upgrades
---

### Post by frotscher2 on 2013-11-12
Hi,

I've a puzzling issue here and would like to find a solution for that. I was about to install a modified Ubuntu 10.04 (called CAELinux) in parallel to a Windows 7 on my system. I did this several times on different Hardware. This is the first time that the following problem occurs.

During installation (via LiveDVD) Ubuntu 10.04 doesn't recognize my devices, i.e. gparted doesn't show anything but a grey background, stating "No device detected". Although I definetely want to install the CAELinux (Ubuntu 10.04) I tried installing a standard Ubuntu 12.04 and succeeded. Its disk utility shows two ATA HDDs. One of them contains Windows 7, the other contains Ubuntu 12.04. Then I thought that the Ubuntu 12.04 fixed the problem but unfortunately, trying to install Ubuntu 10.04 still fails due the same reason as before. Moreover neither Ubuntu 12.04's fdisk nor gparted detect any devices which is strange to me because the installation was successfull.

I've been reading a lot of threads here in the forum concerning the "No device detected" problem but none of them concerns a case like this, in which Ubuntu 12.04 recognizes the HDDs (during installation but not after the installation) but Ubuntu 10.04 doesn't. In those threads a wide range of ideas have been given how to solve the problem but I've no idea where to start, i.e. what's most promising.

Therefor I would like to ask you for advice. I already described my case and would like to append some more information from fdisk or sth. similar but as already mentioned: "fdisk -l" shows empty output. Luckily at least the disk utility shows something (in Ubuntu 10.04 not even the disk utility detected the peripheral devices) and I want to share some information about the HDD and the partitions with you:
[ATTACH=CONFIG]247784[/ATTACH]
Of course I'm willing to provide more information but I don't know which you need in order to help me. 

I'm happy for any suggestions how to start fixing this.

Best regards,

Ralf

---

### Post by fantab on 2013-11-12
Boot with Ubunt Live DVD/USb and post the output of:

```
sudo fdisk -l
sudo parted -l
```

Did you change the Partition table on the HDD in question?
Is RAID involved in the picture?

---

### Post by frotscher2 on 2013-11-13
First I would like to answer your questions. 
> Did you change the Partition table on the HDD in question?
Both HDDs are in question as both cannot be seen by the operating system. On both HDDs I manually created partitions during installation of the respective operating system. I do not know whether this is what you mean by changing the partition table.
> Is RAID involved in the picture?
There is a RAID controller in the system but it is not used.

Here are the requested outputs
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5cdc7b94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              36       65987       32976   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       73728     1605631      765952    7  HPFS/NTFS/exFAT
/dev/sda3         1605632  1953521663   975958016    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5cdc7bd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   585936895   292967424   83  Linux
/dev/sdb2       585938942   710936575    62498817    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5       585938944   710936575    62498816   82  Linux swap / Solaris

```
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      18.4kB  33.8MB  33.8MB  primary  fat16        diag
 2      37.7MB  822MB   784MB   primary  ntfs         boot
 3      822MB   1000GB  999GB   primary  ntfs


Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  300GB  300GB   primary   ext4            boot
 2      300GB   364GB  64.0GB  extended
 5      300GB   364GB  64.0GB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           


```
Thank you very much for trying to help me!

---

### Post by fantab on 2013-11-13
Are able to boot into Windows?
Get into BIOS setup and check what mode is SATA set to. It should be **AHCI**. [I suspect it to be set to RAID]

I think you are using Installer to auto create partitions, you don't have to. You have lots of space. Do it manually and use 'Something Else' option to direct your ubuntu/linux install to those partitions.
For **/dev/sdb**
25GB Primary EXT4 '/'
25Gb Primary EXT4 -- [To install any other distro like Ubuntu 12.04 or Caelinux]
25GB Primary EXT4 -- [Keep it free, in case you need it in future]
All the remaining GB EXTENDED
4-8GB Logical SWAP
All the remaining GB Logical EXT4 [a common Linux DATA partition. Don't use this for /home] 

Also in /dev/sda, its NOT a good idea to keep your DATA in C: with all the Windows system files... If you can, then make C: smaller, like 75-100GB and create another Partition for your DATA [NTFS]. This Partition you can safely share between Linux and Windows without running the risk of damaging Windows system files, if and when you access them from Linux.
See [**Here**]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html") on how to 'Shrink' Windows Partition.

My two cents....

---

