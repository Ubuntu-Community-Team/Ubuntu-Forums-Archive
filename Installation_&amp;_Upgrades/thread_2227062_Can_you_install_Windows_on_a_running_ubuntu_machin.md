---
title: "Can you install Windows on a running ubuntu machine for dual boot?"
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by majk2 on 2014-05-30
Hi
I originally attempted to load Ubuntu onto my Windows machine to achieve a dual boot environment but the process kept failing and I was having difficulty understanding all the drive and partition mumbo jumbo. 
So finally I ended up just doing a fresh install and overwriting my Windows partition. I have been using Ubuntu now on my machine for a couple of weeks and am loving it. 
But every now an then there is some little issue I have with a client that requires me to use a Windows machine. 

So I would now like to attempt installing Windows again as a partitioned dual boot. Can this be done? and if so how?

---

### Post by oldfred on 2014-05-30
Yes, but different for each:
BIOS or UEFI?
What version of Windows?
How many partitions are used?
Post this:
sudo parted -l

If a desktop much better to install in a separate internal drive. Windows only installs to internal drives, not an external USB drive or flash drive.

Often easier to install Windows first, then install Ubuntu in the same boot mode UEFI or BIOS, if on same drive, but you can install afterwards.

---

### Post by majk2 on 2014-06-13
I get this when I "[COLOR=#000000]sudo parted -l"
[/COLOR]
Model: ATA WDC WD5000BEKT-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   500GB  500GB  extended
 5      257MB   500GB  500GB  logical




Model: ATA ST9500420AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2
 2      257MB   500GB  500GB  extended
 5      257MB   500GB  500GB  logical




Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 8573MB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0,00B  8573MB  8573MB  linux-swap(v1)




Error: /dev/mapper/ubuntu--vg-swap_1: unrecognised disk label             


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 491GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0,00B  491GB  491GB  ext4




Error: /dev/mapper/sdb5_crypt: unrecognised disk label


I must admit the Partitions might be in a bit of a mess. I have two harddrives and intended installing Ubuntu onto the second drive leaving Windows on my first drive but somehow after two failed dual boot installs I just thought stuff it and did a override install of Ubuntu. The whole partition labelling exercise left me very confused and I have to admit most of the resources I researched left me even more confused. What I believe has happened that Ubuntu has installed onto the second drive but only onto a partition on that drive. I would dearly love to clean it all up but have been working on Ubuntu for over a month now (Loving it) and would not like to loose what I have already done and set up. I must admit that Ubuntu just works, the only issue I have is a bluetooth driver issue but considering how long it originally took me to get all the drivers loaded and working when I first loaded Windows7, Ubuntu is a dream.

So if you can use the info above to guide me in possibly cleaning up my partition/drive mess and assist me to install Windows7or 8 on the Other harddrive I would be much obliged.

ie. I would like to use the first drive for Windows and the second drive (The whole drive not just a partition) for the already installed Ubuntu 14.04

---

### Post by oldfred on 2014-06-13
I do not know how you installed either, that is not standard. 
It may be RAID or LVM neither of which I know anything about.
/dev/mapper could be RAID or LVM but if full drive encryption it then is the LVM with full drive used as an encrypted volume and you have lvm partitions inside the LVM volume. Makes for a more complicated install but some like the ease of repartitioning that LVM gives. But you use LVM tools not standard partition tools.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

I only know dual boot. But if only using Windows occasionally and do not need speed but flexibility to get into Windows I see many suggest using Virtual memory install. Windows then is running at the same time and can be switched to easily while still in Ubuntu. But you need a bit better hardware and more RAM as that is shared. And not quite as fast so not good for those running games.

[https://help.ubuntu.com/community/VirtualBox/Installation](https://help.ubuntu.com/community/VirtualBox/Installation)
 [http://www.oracle.com/technetwork/server-storage/virtualbox/overview/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/overview/index.html)

---

