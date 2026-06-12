---
title: "New hard drive image using same space?"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by deba on 2006-11-02
Hi,

When I installed ubuntu onto my system initally I installed it to an old 20gb IDE drive connected to IDE1 master on my systemboard and left my 80gb sata windows drive intact. As I now use ubuntu more than windows i decided to install a bigger drive, so i put in a 200gb IDE drive in and used a drive image program to copy the 20gb drive image onto the new 200gb drive. After rebooting everything is fine but i still cant access the remaining space on the drive as it seems to be another volume. fdisk -l shows the following:-

Disk /dev/sda: 80.0 GB, 80032038912 bytes
44 heads, 63 sectors/track, 56389 cylinders
Units = cylinders of 2772 * 512 = 1419264 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       57750    80041468+   7  HPFS/NTFS

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda3            2435       24321   175807327+  83  Linux
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

What can i do to use the remaining space on /dev/hda3 as my /home directory?. Do i need to backup my data on /dev/hda1 (Possibly to the windows disk /dev/sda1) and reformat?. Whats the easiest way?.
Thanks.

---

### Post by Kateikyoushi on 2006-11-02
Follow this guide to move your home to the new partition. [LINK]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by deba on 2006-11-03
Thanks Kateikyoushi,

Worked a treat!!

---

