---
title: "recommended disk partition for kubuntu 14.04 manual install &amp; dual boot"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by marisalee on 2014-04-19
What is the recommended disk partition for kubuntu 14.04 manual install and dual boot with Windows 8.1 64 bit?

My computer has 6GB RAM and Windows 8.1 64 bit.
I try to install kubuntu 14.04 64 bit by manual disk partition.
My current disk has 283GB Free Space.
(parted) print free 
```
Model: ATA WDC WD10EZEX-22B (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system  Name                          Flags
        17.4kB  1049kB  1031kB  Free Space
 1      1049kB  840MB   839MB   ntfs         Basic data partition          hidden, diag
 2      840MB   1113MB  273MB   fat32        EFI system partition          boot
 3      1113MB  1247MB  134MB                Microsoft reserved partition  msftres
 4      1247MB  162GB   161GB   ntfs         Basic data partition          msftdata
 5      162GB   700GB   538GB   ntfs         Basic data partition          msftdata
        700GB   983GB   283GB   Free Space
 6      983GB   1000GB  16.9GB  ntfs         Basic data partition          hidden, diag
        1000GB  1000GB  729kB   Free Space

```

---

### Post by oldfred on 2014-04-19
Partitioning is very personal depending on what you plan to do and level of experience.
A new user is fine with the default install of just / (root) and swap. 
Then you may want to add /home or data partitions but adding Linux data partitions also requires setting ownership & permissions and perhaps manually mounting it or editing fstab. Often beyond what a new user should be doing.

My typical suggestion, adjust as you desire:
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

If your Windows is pre-installed or UEFI, be sure to review all the suggestions in link in my signature.

---

