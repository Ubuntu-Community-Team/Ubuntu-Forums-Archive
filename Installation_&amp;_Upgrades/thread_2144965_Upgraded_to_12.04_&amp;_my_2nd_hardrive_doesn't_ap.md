---
title: "Upgraded to 12.04 &amp; my 2nd hardrive doesn't appear anymore"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by Ed W. on 2013-05-13
I upgraded to 12.04 LTS and installed the updates, but my second hard drive doesn't appear anymore.  How make it appear?  Its not listed under Devices like my other hdd.  But it does appear in the Bios.

---

### Post by Bashing-om on 2013-05-13
hi ! Ed W.

Do you mean to say that the 2nd hard drive does not even appear in the file manager ?
How do you want the drive to mount - manually on demand, or automount on startup ?
Please provide the output of terminal codes:
```
sudo fdisk -lu
sudo blkid
cat /etc/fstab
```

and we will see what we can do.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by Ed W. on 2013-05-14
Bashing-om,

Yes, the 2nd hdd doesn't appear in the file manager.  And I'd like to mount it on demand.  Thanks for the help. 

'Sudo fdisk -lu' gave me the following:

 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x000751ae 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *          63   976751999   488375968+   7  HPFS/NTFS/exFAT 
  
 WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted. 
  
  
 Disk /dev/sdb: 61.5 GB, 61492838400 bytes 
 255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0xbad2bad2 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdb1            2048   103327743    51662848   83  Linux 
 /dev/sdb2       103329790   120102911     8386561    5  Extended 
 /dev/sdb5       103329792   120102911     8386560   82  Linux swap / Solaris 
 ----------------------------
 'sudo blkid' gave me:
  
 /dev/sda1: UUID="0E08F04108F028FB" TYPE="ntfs"  
 /dev/sdb1: UUID="beb4d5b2-2bfa-46df-95bc-e13d2d6b7fee" TYPE="ext4"  
 /dev/sdb5: UUID="3f81a1b1-f2c0-4ac0-a5d7-7fb74f6254c1" TYPE="swap"  
 

 -----------------
  'cat /etc/fstab ' gave me :
 

 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid' to print the universally unique identifier for a 
 # device; this may be used with UUID= as a more robust way to name devices 
 # that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    nodev,noexec,nosuid 0       0 
 # / was on /dev/sdb1 during installation 
 UUID=beb4d5b2-2bfa-46df-95bc-e13d2d6b7fee /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sdb5 during installation 
 UUID=3f81a1b1-f2c0-4ac0-a5d7-7fb74f6254c1 none            swap    sw              0       0

---

### Post by Bashing-om on 2013-05-14
Ed W.

If you do not see your Windows' partition in ubuntu's file manager, there is a problem we will have to explore:
> 

 
 
**Using the File Manager**

 For  those using a desktop version of Ubuntu, or one of its offical  derivatives, the easiest and quickest way of mounting NTFS or FAT32  partitions is from the file manager: Nautilus in Ubuntu, Thunar in  Xubuntu, Dolphin in Kubuntu and PCManFM in Lubuntu. Simply look in the  left pane of the file manager for the partition you wish to mount and  click on it - it will be mounted and its contents will show up in the  main pane. Partitions show with their labels if labelled, or their size  if not. 
Unless  you require your Windows partition - or a NTFS/FAT32 partition for data  shared with Windows - mounted every time you boot up for one of the  reasons given below, mounting from the file manager in this way should  suffice.

In your "fdisk" output the header info for "sda" is not present, I would like to see it; Merely for verification reasons - I am surprised to only see one partition on that first disk - sda ->NTFS Windows -. The second disk - sdb -> ext4 (Linux) - contains your ubuntu installation.

Post complete output of terminal code:
```
sudo fdisk -lu
```[INDENT]
everything will come up rosy

[/INDENT]

---

