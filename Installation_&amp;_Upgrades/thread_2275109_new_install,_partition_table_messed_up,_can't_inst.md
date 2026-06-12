---
title: "new install, partition table messed up, can't install grub"
date: 2015-04-24
forum: Installation &amp; Upgrades
---

### Post by J_Me on 2015-04-24
In brief, I installed kubuntu 14.04.2 but can't install the grub bootloader.

Steps taken
1- built grub on another computer and copied it over to a usb with the kubuntu iso file.(because of UEFI and Atom chips)
2- installed kubuntu with 'guided use whole disk'
3- booted into the fresh install and built grub again but I get an error.

grub error snippet
```
me@here:~/grub$ cd grub-core
me@here:~/grub/grub-core$ ../grub-install -d . --efi-directory /boot/efi/ --target=i386
Installing for i386-efi platform.
../grub-install: warning: disk does not exist, so falling back to partition device /dev/mmcblk0p1.
../grub-install: warning: disk does not exist, so falling back to partition device /dev/mmcblk0p1.
../grub-install: warning: disk does not exist, so falling back to partition device /dev/mmcblk0p1.
../grub-install: error: disk `hostdisk//dev/mmcblk0p1' not found.
me@here:~/grub/grub-core$ 

```
fdisk -l
```
me@here:~$ sudo fdisk -l
[sudo] password for me: 

WARNING: GPT (GUID Partition Table) detected on '/dev/mmcblk0'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mmcblk0: 31.3 GB, 31272730624 bytes
255 heads, 63 sectors/track, 3802 cylinders, total 61079552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb05f7380

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1    61079551    30539775+  ee  GPT

Disk /dev/mmcblk0boot1: 4 MB, 4194304 bytes
4 heads, 16 sectors/track, 128 cylinders, total 8192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mmcblk0boot1 doesn't contain a valid partition table

Disk /dev/mmcblk0boot0: 4 MB, 4194304 bytes
4 heads, 16 sectors/track, 128 cylinders, total 8192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mmcblk0boot0 doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 7553 MB, 7553777664 bytes
256 heads, 63 sectors/track, 914 cylinders, total 14753472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes                                                                                 
I/O size (minimum/optimal): 512 bytes / 512 bytes                                                                                     
Disk identifier: 0x1da45175                                                                                                           
                                                                                                                                      
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
me@here:~$


```
I did some poking around with the partition manager and also using a live usb.A couple of things that really stand out is my hard drive is listed as  ntfs and that I have a restore partition of 7 gigs with windows files  inside. I've taken snapshots as it's difficult to explain what's going on. I can upload the pictures if needed.

Thanks
specs
asus tranformer t100
intel atom processor
32gig SSD

---

### Post by oldfred on 2015-04-24
Fdisk does not work on gpt partitioned drives. Use parted or gdisk.
You have to have gpt partitioned drive to install in UEFI boot mode.
Will you be dual booting with Windows? It only boots in UEFI mode from gpt partitioned drives.

Do not know details of 32 bit UEFI other than originally Linux did not support it and that may be why Windows created a 32 UEFI for 64 bit systems. Just to prevent Linux installs.

       Instructions to install Ubuntu 14.10 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)
Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
Sound issues on Bay Trail
[http://ubuntuforums.org/showthread.php?t=2255425](http://ubuntuforums.org/showthread.php?t=2255425)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

Most of the links in my signature below are just for 64 bit standard installs. But some general info on UEFI may be useful.

---

### Post by J_Me on 2015-04-24
Thanks for the reply
This is what parted says running from a live usb
```
kubuntu@kubuntu:~$ sudo parted -l
Warning: Unable to open /dev/sda read-write (Read-only file system).  /dev/sda
has been opened read-only.
Model:  USB DISK 2.0 (scsi)
Disk /dev/sda: 7554MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  7553MB  7552MB  ntfs         Basic data partition  hidden, diag


Model: SanDisk Cruzer (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  16.0GB  16.0GB  fat32              boot


Error: /dev/mmcblk0rpmb: unrecognised disk label                          

Error: /dev/mmcblk0boot0: unrecognised disk label                         

Error: /dev/mmcblk0boot1: unrecognised disk label                                                                                     
                                                                                                                                      
Model: MMC HBG4e (sd/mmc)                                                                                                             
Disk /dev/mmcblk0: 31.3GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   29.2GB  28.7GB  ext4
 3      29.2GB  31.3GB  2027MB  linux-swap(v1)


kubuntu@kubuntu:~$ 

```
> Instructions to install Ubuntu 14.10 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
Yes that's the tutorial I followed and only got stuck on the last part of installing grub on this machine.
> Will you be dual booting with Windows? It only boots in UEFI mode from gpt partitioned drives.
No just kubuntu
> You have to have gpt partitioned drive to install in UEFI boot mode.
So what would the easiest thing be. To reinstall kubuntu after I've formatted and partitioned the drive to GPT using parted/gdisk or can I fix the current situation without reinstalling.
> Do not know details of 32 bit UEFI other than originally Linux did not support it and that may be why Windows created a 32 UEFI for 64 bit systems. Just to prevent Linux installs.
It's possible, I've heard of microsoft doing underhanded things in the past just out of spite.

Thanks

---

### Post by oldfred on 2015-04-24
It already shows the MMC as gpt partitioned with the FAT32 formatted partition with boot flag to be the ESP - efi system partition.

So drive looks like it is configured correctly. But I do not know about Disk label error?
Try gdisk just to see if it reports different errors or use it to rewrite gpt partition table. 
       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by J_Me on 2015-04-25
Arrrrrrrgh........ grub installed OK, stupid error on my part.

@oldfred Thanks for your help things look clearer now. So this laptop does have a second internal hard drive and it's used for restoring windows. Sometimes I can't see the wood for the tree's lol.

Thanks again

---

### Post by turova on 2015-05-02
Could you please (always) post the solution now that you've figured it out? I'm making the same stupid error...

Edit: Ahh, right... Needed to use "**sudo** ../grub-install -d . --efi-directory /boot/efi/ --target=i386".

---

