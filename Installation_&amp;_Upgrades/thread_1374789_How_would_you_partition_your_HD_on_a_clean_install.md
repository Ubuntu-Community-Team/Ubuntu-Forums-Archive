---
title: "How would you partition your HD on a clean install?"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by Cotopaxi on 2010-01-07
I made an upgrade from Kubuntu 9.04 to 9.10 and this upgrade generated a series of permission problems. 

Considering that I have an individual /home partition, I am planning to make a clean install of Karmic (9.10) on a laptop with a
230GB hard disk and 2GB RAM.

The actual hard disk is mounted the following way:

Partition------File System------Mount Point-----Size
/dev/sda1------ext4-------------/home-----------204.89GB
/dev/sda2------ext4-------------/-----------------9.36GB
/dev/sda3------linux-swap-------------------------1.86GB
   /dev/sda5---fat32------------/dos-------------16.77GB

In total there are some 230GB of Hard Disk available.

The fat 32 partition was not a good idea, because I can't access it from the file manager, so I will dump this partition on my next installation.

Now my question:

What partitions would you recommend to mount and what size would you give to each partition?

Thanks for your help!

---

### Post by slakkie on 2010-01-07
10 GB root sounds good.
Depending on your needs I would also create a seperate moint for /opt and perhaps even /usr. If you have a seperate slice for /usr then you can reduce the size of your root, since all applications are installed in /usr. 

Eitherway, my layout:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6c5f6c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  83  Linux # Seperate grub partition
/dev/sda2               9        1028     8193150   83  Linux # Debian root
/dev/sda3            1029        2048     8193150   83  Linux # Ubuntu root
/dev/sda4            2049        9729    61697632+   5  Extended
/dev/sda5   *        2049        3068     8193118+  83  Linux # Designated for test installs + additional storage when needed.
/dev/sda6            3069        3323     2048256   82  Linux swap / Solaris
/dev/sda7            3324        3361      305203+  83  Linux # /var/log
/dev/sda8            3362        3552     1534176   83  Linux # /opt
/dev/sda9            3553        9729    49616721   83  Linux # /home

```

---

### Post by tommcd on 2010-01-07
If Ubuntu is the only OS on the system then I would only use root, swap, and home. A 10-15GB root partition is plenty. Your 10GB root should be good though, unless you plan on installing tons of software, including some big 3D games like Doom3 and Quake4, etc. These games take up about 2GB each, so you may need a larger root if you want a lot of games. Those games can also be installed and run from your home directory though. 
My root directory for Ubuntu has never been larger than about 3.5GB, unless I had some games like Doom3 or Quake4 on it.
The fat32 partition is of no use unless you plan to share files with a Windows system.

---

### Post by Cotopaxi on 2010-01-07
Thanks both for your replies!

Actually I am not routined enough to go Slakkie's way, I am a Kubuntu user since 2007.

So I will mount a 10-15GB root partition, a 2GB swap partition and the rest for home.

Thanks very much indeed again!

---

### Post by prshah on 2010-01-07
> **Cotopaxi said:**
> a 10-15GB root partition, a 2GB swap partition and the rest for home.

10-15GB for "/" is fine, but I recommend you use 2.5~3 GB for swap if you are planning to use the hibernate feature. This is because when you hibernate, your current RAM contents are dumped to the swap partition. The extra space is to make allowances for stuff that may already be in the swap, future bad sectors, etc.

Also, putting your "/home" at the last is good, because if you transfer your install to a new, bigger, hard disk, it will become very easy for you to resize your "/home".

---

