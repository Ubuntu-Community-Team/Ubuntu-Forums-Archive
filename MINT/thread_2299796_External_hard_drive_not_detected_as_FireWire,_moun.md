---
title: "External hard drive not detected as FireWire, mounts as USB"
date: 2015-10-21
forum: MINT
---

### Post by Justin_Snow on 2015-10-21
I'm brand new to Linux, so please bear with me.


Just installed Linux Mint to an old iMac and tried to attach my external drive (that I've been using on my MacBook for years) via FireWire to no avail. It's not even being detected, let alone mounting. However, if I plug it in via USB, it mounts just fine. No idea what's going on. Tons and tons of Googling. I've learned some of the info that would help you help me, so here's what I have below. Let me know if there's anything else I can share that would make things more clear.


All of this is with the drive plugged in via FireWire.


```

$ sudo fdisk -l


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1     1050623      525311+  ee  GPT
/dev/sda2   *     1050624   968392703   483671040   83  Linux
/dev/sda3       968392704   976771071     4189184   82  Linux swap / Solaris

```


```

$ lsblk


NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0 461.3G  0 part /
&#9492;&#9472;sda3   8:3    0     4G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom

```


```

$ sudo blkid
/dev/sda1: UUID="166C-3BDF" TYPE="vfat" 
/dev/sda2: UUID="7762e9bb-9897-484c-abc7-0df43e009ae2" TYPE="ext4" 
/dev/sda3: UUID="c30ff546-f5ae-401a-89eb-7ce5bc41ecb5" TYPE="swap"

```


```

$ dmesg | grep -i fire
[    2.156648] firewire_ohci 0000:03:00.0: added OHCI v1.10 device as card 0, 8 IR + 8 IT contexts, quirks 0x10, physUB
[    2.692194] firewire_core 0000:03:00.0: created device fw0: GUID 001f5bfffe0919bc, S800

```


```

$ sudo lshw | grep -i fire
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW643 [TrueFire] PCIe 1394b Controller
                configuration: driver=firewire_ohci latency=0

```


```

$ lsmod | grep -i fire
firewire_ohci          40551  0 
firewire_core          68769  3 firewire_ohci
crc_itu_t              12707  1 firewire_core

```


And just so you believe me, here's proof it works via USB.


```

$ sudo fdisk -l


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1     1050623      525311+  ee  GPT
/dev/sda2   *     1050624   968392703   483671040   83  Linux
/dev/sda3       968392704   976771071     4189184   82  Linux swap / Solaris


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3000.6 GB, 3000558944256 bytes
255 heads, 63 sectors/track, 364797 cylinders, total 5860466688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967294  2147483647   ee  GPT
Partition 1 does not start on physical sector boundary.

```

---

### Post by howefield on 2015-10-21
Thread moved to the "*MINT*" forum.

---

### Post by yancek on 2015-10-21
Take a look at the link below at the kernel.org site for Linux, specifically dealing with firewire.  It's been supported for years but I doubt it is enable by default.  I don't use Apple computers so can't help with that.  The FAQ has a lot of info.  Good luck.

[https://ieee1394.wiki.kernel.org/index.php/Main_Page](https://ieee1394.wiki.kernel.org/index.php/Main_Page)

---

### Post by Justin_Snow on 2015-10-21
> **yancek said:**
> Take a look at the link below at the kernel.org site for Linux, specifically dealing with firewire.  It's been supported for years but I doubt it is enable by default.  I don't use Apple computers so can't help with that.  The FAQ has a lot of info.  Good luck.

[https://ieee1394.wiki.kernel.org/index.php/Main_Page](https://ieee1394.wiki.kernel.org/index.php/Main_Page)

Thanks, yancek. I was searching on that page a bit before posting here but I didn't come across the "My FireWire hardisk/CD-ROM/DVD-Recorder is not recognized. Now what?" section of the FAQ, which is perfectly relevant. I'll try their suggestions once I get home from work.

---

### Post by Justin_Snow on 2015-10-24
Followed instructions on the wiki's FAQ, specifically the "My FireWire hardisk/CD-ROM/DVD-Recorder is not recognized. Now what?" part. nothing has changed. anyone have other ideas?

---

