---
title: "Moving GRUB2 to my Linux HDD"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by kappel79x64 on 2011-04-11
Hello,

i have 3 HDD`s in my PC, 

[LIST=1]
[*]320GB Samsung Sata (Win7 Boot sda1)
[*]500GB WD Blue Sata (Linux home swap sdc 1 2 5)
[*]1TB Datastoragecentermillenium 2000 (storage sdb1)
[/LIST]

my plan is to get rid of the 320GB hdd, as far as i have seen Grub 2 is installed on my 500GB HDD so i wont have to change that i think. 

The only thing is when i disable the 320, Grub does not start, so i need to change that.

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaad0c01b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568832    7  HPFS/NTFS/MonkeyFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4902cf75

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c11dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       58336   468581376   83  Linux
/dev/sdc2           58336       60802    19802113    5  Extended
/dev/sdc5           58336       60802    19802112   82  Linux swap / Solaris

```ubuntu 10.10 x64, bootmanager should be grub2

```
grub-install (GRUB) 1.98+20100804-5ubuntu3
``````
xxx:~$ sudo grub-probe -t device /boot/grub  === /dev/sdc1

```i think all i need to do is make the sdc1 bootable and maybe change or rebuild grub2?

cheers and thx

---

### Post by Dutch70 on 2011-04-11
This should help. 
[[COLOR="Red"]https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

It looks like the commands you will need to run are...
```
sudo mount /dev/sdc1 /mnt
```
and...
```
sudo grub-install --root-directory=/mnt /dev/sdc
```

However, I went through this rather quickly, so check it carefully before you do it.

.

---

### Post by oldfred on 2011-04-11
If you can still boot into your system you can just run the install command from there to any MBR. You then have to change BIOS to boot that drive.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

I prefer to have grub2's bootloader in the MBR of the drive with the system. But I have Ubuntu on every hard drive  because of these comments.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive. I keep old install, current install, & beta/next install as working systems.

---

### Post by kappel79x64 on 2011-04-12
Hello,

thx for all the answers !


i have done so far :

sudo grub-install /dev/sdc

```
Installation finished. No error reported.
```

sudo update-grub

```
Generating grub.cfg ...
Found background: /usr/share/images/grub/BonsaiTridentMaple.tga
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-27-generic
Found initrd image: /boot/initrd.img-2.6.35-27-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

Found Win7 .....zzzzzz

sudo dpkg-reconfigure grub-pc

```
Installation finished. No error reported.
Generating grub.cfg ...
Found background: /usr/share/images/grub/BonsaiTridentMaple.tga
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-27-generic
Found initrd image: /boot/initrd.img-2.6.35-27-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

i have klicked return on all pages like you wrote, sdc for boot and not a partition like sdc1. i hope the default was ok so i can boot now

```
grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD5000AAKX-001CA0_WD-WCAYUD044995
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10

```


hope thats all right, like the Linux command, its empty 

bye

---

### Post by kappel79x64 on 2011-04-12
Hello,

back again it worked great, oldfred.

there is still a win7 entry but who cares. i can boot from the linux sdc drive now while sda is disabled. great, now i can install another linux distro on the sda :) or move my /home to sda but i am not sure how safe that is, on the other hand a new ubuntu is copming soon so i could reinstall all new and change then /home with the new installation, maybe oldfred you have a solution for moving /home aswell :)

but still, ubuntu didnt create a /home as default, thats really annoying now as the system grows and so /home,

---

### Post by Dutch70 on 2011-04-12
See if this site helps, but read it carefully, I think it's a little dated. For example, it advises ext3, you probably want ext4. Either way, it's a great site & usually offers some great info, so I thought I'd offer the link.
[[COLOR="DarkOrange"]Create a separate home partition in Ubuntu[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")
The first link on that site is a good one also.
[[COLOR="DarkOrange"]https://help.ubuntu.com/community/Partitioning/Home/Moving[/COLOR]]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

This one is for creating a separate /home during installation.
[[COLOR="DarkOrange"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

Thanks oldfred for the tip on reinstalling Grub2 from a working system. 
That will save me a lot of time.

---

### Post by oldfred on 2011-04-12
Dutch's link is good, I think it was the one I used but I reviewed several. To get the separate /home during an install you have to use manual install, create partitions (although I create in advance), and tell it then which partition is / (root) and its format & which is /home and its format if new or check do not format if reusing an existing /home.

I prefer to have an entire system including /home on one drive. Data or other systems then are on other drives. Each drive also has that systems bootloader in the MBR, so each drive can work if all the other drives are missing/broken etc.

---

### Post by kappel79x64 on 2011-04-12
Thx dutch and oldfred !

a linux on every hdd with bootloader sounds good, but i am not sure how to do that, i am thinking of installing a debian on the new old win7 hdd now, its pretty big with 320gb, for ubuntu i use 500gb lol. but i never installed more than 1 linux at a time, but i have seen and heard of people with many many linux installations on just 1 hdd.

i will read more into that knoppix on every hdd, and the other good links you both gave me.

cheers

---

