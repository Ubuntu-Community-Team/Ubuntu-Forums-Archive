---
title: "Installing Grub in partitian Windows 7"
date: 2013-11-14
forum: Installation &amp; Upgrades
---

### Post by douglas.e.ryan on 2013-11-14
I'm trying to install on a Windows 7 machine that already has four primary partitions that uses MBR and I need help to install this without risking making the machine unbootable. The computer will not allow me to make a restore disc because the HDD isn't the default configuration.  The drive looks like:

sudo parted  /dev/sda unit s print
Model: ATA WDC WD10EADX-22T (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End          Size         Type     File system     Flags
 1      2048s       36866047s    36864000s    primary  linux-swap(v1)  diag
 2      36866048s   37070847s    204800s      primary  ntfs            boot
 3      37070848s   378200063s   341129216s   primary  ntfs
 4      378204160s  1953523711s  1575319552s  primary  ntfs

As you can see, I already have swap partition from an earlier install. Number 2 is "System Reserved." Three is the "C" drive and four is where I have other data. Would it be safe to just install into number four and just have Grub in a folder and just use the Windows boot menu to Ubuntu (realizing I might need to use EasyBCD to add it to the menu?)

Here's another look the drive, in case it helps:

fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes, 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x35d5c1f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    36866047    18432000   27  Hidden NTFS WinRE
/dev/sda2   *    36866048    37070847      102400    7  HPFS/NTFS/exFAT
/dev/sda3        37070848   378200063   170564608    7  HPFS/NTFS/exFAT
/dev/sda4       378204160  1953523711   787659776    7  HPFS/NTFS/exFAT

---

### Post by douglas.e.ryan on 2013-11-14
In case I didn't make it clear, I'm trying to keep the MBR and "C" drive intact at least until I can confirm everything works properly (drivers, my DSL connection, interoperability between Libre Office for Linux and Word 2013, etc)

---

### Post by Mark Phelps on 2013-11-14
The only way you can install Ubuntu to an NTFS partition is using Wubi -- which I wouldn't recommend because it's been discontinued.

I'm also concerned that parted says that sda1 is linux-swap but fdisk says the same partition is NTFS.  They can't BOTH be true.

Also, if you do decide to install inside Win 7 using Wubi, do NOT, repeat, NOT force the installation of GRUB.  Wubi installs use something know as GRUB4DOS -- a version of GRUB that can be installed to, and run from, a Windows filesystem.  If you force the installation of GRUB, you risk corrupting Win7 boot.

---

### Post by oldfred on 2013-11-14
Since they are discontinuing wubi as it does not work with gpt partitioned drives which all new UEFI system have, the suggestion is just to use flash drive with persistence. While a flash drive and USB port make it a bit slower than hard drive it lets you run system. And since Linux caches recent activity into RAM and most new systems have lots of RAM system still runs ok. It will be a bit slow loading a large app or saving data.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)

---

### Post by douglas.e.ryan on 2013-11-14
Oh, I was gonna reformat sda4  as EXT4, so that won't be a problem. Minitools Partition Wizard agrees that sda1 is swap partition and I did have Linux on this drive before. Windows Disk Management seems to think sda1 is some kind of recovery partition.

---

### Post by oldfred on 2013-11-14
Make sda4 an extended partition and then you can have many logical partitions inside the extended. Windows is the one that has to boot from a primary partition. Windows second installs even can be in logical partitions, but have no boot files as they will be in primary partition only.

---

### Post by douglas.e.ryan on 2013-11-15
I think I got it, thanks guys. Let me just confirm how to do this, though. After backing up all existing sda4 data, I just need convert it a logical partition (there doesn't seem to be an option for "Extended" unless I missed it) and install there. I'd also be able to make another logical partition for swap to address the concern that sda1 might not really swap partition with risking creating Dynamic Disks. Am I right about this?

---

### Post by oldfred on 2013-11-15
Sounds correct. 
If you create logical partitions they will be in the extended and all logicals have to be in one extended partition. If you have enough space you can create a shared NTFS as logical also and restore some or all of your current data and use it in both systems.
Only if hibernating which really is not recommended when dual booting do you need swap equal in size to RAM in GiB (not GB) so all of RAM would fit. Otherwise if you have 4GB of RAM or more some swap is suggested just in case but probably will not be used. I suggest 2GB just to have some.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

