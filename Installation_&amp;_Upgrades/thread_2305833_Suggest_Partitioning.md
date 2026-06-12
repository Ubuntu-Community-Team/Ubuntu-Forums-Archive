---
title: "Suggest Partitioning"
date: 2015-12-09
forum: Installation &amp; Upgrades
---

### Post by Jesse_L. on 2015-12-09
I have a laptop that has the following drives. 500Gb HDD (sda) and 250Gb SSD (sdb) as identified by Ubuntu. I would like to boot Ubuntu from the SSD. What would be the suggested layout of partitions based upon the experience of the experts in the forums?

---

### Post by oldfred on 2015-12-09
I like to throw my 2 cents in, but partitioning depends a lot on each user that what they want or plan to use system for. And even my own optimal partitioning is often not so good several years later, but by then I often have a new hard drive (do not trust them for too long) as main working drive.

Is system UEFI or BIOS?
Are you installing other operating systems, particularly Windows? Windows only boots from gpt with UEFI, so if BIOS, you will have to have MBR(msdos) partitioning.

I like to have Ubuntu on every drive and have several copies on larger drive for testing. I like to try new version before converting. I have 14.04 on SSD & HDD. HDD also has 15.10. And I just installed 16.04 on SSD which will be my working system after it is released, but I may do clean re-install then.

If only Ubuntu, I also suggest gpt partitioning. Or if UEFI you must have gpt partitioning. Or if drive may later be moved to an UEFI system, better to use gpt now or else you may have to totally reformat later.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/581902/how-to-efficiently-partition-a-single-windows-ubuntu-dual-boot-disk](http://askubuntu.com/questions/581902/how-to-efficiently-partition-a-single-windows-ubuntu-dual-boot-disk)

---

### Post by Jesse_L. on 2015-12-09
OldFred thanks for the response. 

The system is UEFI but dedicated Ubuntu only. My question was more centered around if I should dedicate the SSD to UEFI(GPT)/boot/Kernel and the Spinning Disk to /Home

---

### Post by oldfred on 2015-12-09
If a newer user, it is easier to configure /home on HDD. Ownership & permissions & use of partition are created as part of install.
But if a bit more advanced then separate data partition(s) on HDD and keeping / on SDD makes sense.

This is my current partitioning, note that neither drive is fully partitioned yet:

```
fred@trusy-ar:~$ sudo parted -l
[sudo] password for fred: 
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name     Flags
 1      1049kB  525MB   524MB   fat32           efi      boot
 2      525MB   527MB   2097kB                           bios_grub
 3      527MB   26.7GB  26.2GB  ext4            trusty
 6      26.7GB  53.0GB  26.2GB  ext4            xenial
 5      121GB   126GB   5163MB  ext4            iso_ssd
 4      126GB   128GB   2000MB  linux-swap(v1)


Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  525MB   524MB   fat32           EFI System Partition  boot
 2      525MB   527MB   2097kB                                        bios_grub
 3      527MB   26.7GB  26.2GB  ext4            vivid
 4      26.7GB  446GB   419GB   ext4            data
 5      446GB   476GB   29.9GB  ext4            backup
 9      476GB   501GB   25.0GB  ext4            wily_b
10      501GB   527GB   26.2GB  ext4            trusty_3
 8      711GB   713GB   2000MB  linux-swap(v1)
 7      713GB   993GB   280GB   ext4            homerun
 6      993GB   1000GB  7337MB  ext4            iso_hdd



```

---

