---
title: "Dual boot disk allocation question"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by Taffman on 2011-05-05
I have just installed Ubuntu desktop Linux Lucid 10.4 alongside my Windows Vista Business OS as a first time user. All went well however my PC has a 300GB boot drive ( C: ) and a spare 2TB disk ( E: ). My C: drive is nearly full so when I installed Ubuntu and was asked the question where do you want it installed I chose drive E:. My intention ws to place everything Linux in Drive E: leaving Drive C: alone as it's nearly full.

My problem now is whenever I boot Ubuntu I get an error stating that I only have 416.3MB left. Why is then when I installed Ubuntu on an empty 2TB drive? Looks like the space allocated for Ubuntu is limited in some way perhaps in a partition. How can I make all or a substantial amount of my 2TB drive available to Ubuntu ?

---

### Post by ajgreeny on 2011-05-05
From your running ubuntu can you show the output of ```
sudo parted -l
```and then ```
sudo fdisk -l
```both of those have a lower case L at the end, not figure 1.

---

### Post by Taffman on 2011-05-05
Hi Thanks for the quick reply, this is what I get:

```
sudo parted -l
Model: ATA ST3320633AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs         boot


Model: ATA Hitachi HDS72202 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs


sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbffebffe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd7d3fa3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953512448    7  HPFS/NTFS

```

---

### Post by ajgreeny on 2011-05-05
As you may have gathered from these output texts you appear to have no ubuntu installed at all.

You say you installed alongside your Windows Vista, but I am wondering if you used wubi to install inside windows, ie, did you run the live CD with windows and use it that way.

If that is so, I can not help you any further apart from pointing you to the Wubi megathread link in my signature.  Wubi is really only for use as a test-bed of ubuntu and your hardware, not as a serious dual boot system.

---

### Post by Taffman on 2011-05-05
I booted from the Ubuntu ISO I burned to cd. During the install, it asked if I wanted to install as the only o/s or alongside Windows. I chose the latter. There was no mention of Wink whatever that is.

---

### Post by Dutch70 on 2011-05-05
When you boot your computer, does it say something like this..
```
windows
Ubuntu
```

and you choose one of the 2, or is it more like this...*(not exact, of course)*

```
Ubuntu Maverick Meerkat 2.6.35-28-generic (on /dev/sdb5)
Ubuntu Maverick Meerkat 2.6.35-28-generic (recovery mode) (on /dev/sdb5)
Windows Vista (loader) (on /dev/sdb1)
Windows Vista (loader) (on /dev/sdb3)
```

Or, check in windows programs to see if Ubuntu is installed there. I agree with the above, if you're able to boot into Ubuntu, it's gotta be Wubi aka windows installer.

---

