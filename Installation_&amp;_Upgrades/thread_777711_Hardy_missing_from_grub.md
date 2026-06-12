---
title: "Hardy missing from grub"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Foxblood on 2008-05-01
Hi, here's hopong someone can help.
I was triple booting Ubuntu, Vista and XP happily enough. But could I leave well enough alone? No, I tried to upgrade to Hardy pre-release. It didn't go well. Some kind of nVidia problem, I think. Anyway, I decided to back up my files and install Hardy proper version so as to overwrite the existing problematic install. It seems to have installed but it doesn't show up in the Grub menu and Hardy release candidate still shows. How can I fix this? Ideally, I'd like to complete what I set out to do ie. install Hardy over the existing release candidate version and so keep my triple-boot setup. 
Help, anyone? Thanks in advance.

---

### Post by Pumalite on 2008-05-01
Post:
sudo fdisk -l
cat /boot/menu.lst

---

### Post by Foxblood on 2008-05-01
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf16d6536

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32531   261302240+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           32531       36364    30787584    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           36365       38801    19575202+  83  Linux
/dev/sda4           38802       38913      899640    5  Extended
/dev/sda5           38802       38913      899608+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd66af43a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13035   104703606    7  HPFS/NTFS
/dev/sdb2           13036       19457    51584715    5  Extended
/dev/sdb5           13036       19189    49431973+  83  Linux
/dev/sdb6           19190       19457     2152678+  82  Linux swap / Solaris


cat: /boot/menu.lst: No such file or directory

---

### Post by Pumalite on 2008-05-01
You have a Partition Table problem. Fix it with TestDisk: 
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Foxblood on 2008-05-01
I'm using test-disk now under XP ans I'm a bit confused. 

[IMG]http://i27.tinypic.com/23rk2mv.jpg[/IMG]

Is it set to delete by default? I want to keep the first two, Vista and XP. Everything else has been backed up so I wouldn't mind deleting all Ubuntu partitions and then reinstalling Hardy. However, I've got a strong feeling that I could seriously screw up everything if I make a wrong move at this juncture. 

Any thoughts?

---

### Post by Pumalite on 2008-05-01
It says 'Structure OK.', even though it says this in your fdisk:
'Partition 1 does not end on cylinder boundary'.I don't know what to tell you. Read the documentation.
'

---

