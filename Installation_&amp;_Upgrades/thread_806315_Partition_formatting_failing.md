---
title: "Partition formatting failing"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by mikzdx on 2008-05-24
hey guys,

I am trying to install ubuntu 8.04 on my new computer, but the partitioning phase in the install keeps failing. It stops at 5% and the text underneath says 'Creating ext3 file system for / in partition #1 of SCSI2.' When I then try again, it seems as if the partitions were created, but without anything being installed. Can anyone tell me what I need to do to fix this problem?

My System:
WDC SE16 WD5000AAKS 500GB
GIGABYTE GA-MA790FX-DS5
AMD Phenom 9500 Agena 2.2GHz 4 x 512KB
Kingston HyperX 4GB(4 x 1GB)

---

### Post by Partyboi2 on 2008-05-24
Have you tried to manually setup the partitions before starting the installer? You can do this by selecting "Partition Editor" (System>Admin>Partition Editor) on the live cd. Then create a ext3 /(root) partition and a swap partition about 2 times the size of your installed ram (but you probably wont need more then 2 gig in total) If you are wanting to store your doc's and settings on a seperate partition to make it easier if you need to reinstall in the future I would also suggest creating a seperate /home partition as well. Then restart the installer and use the newly  created partitions and see if that works.

---

### Post by mikzdx on 2008-05-24
when i go into the partition editor and do everything you said, it stalls after 5 seconds or so.

---

### Post by Partyboi2 on 2008-05-25
Is windows the current o/s on the disk? If so try defraging windows a few times. Then run the installer again. Another thing you could try is to boot the live cd and  start gparted (Partition Editor) from a terminal (Applications>Accessories>Terminal) and see what the output returns from the terminal
```
 sudo gparted /dev/sda
```Edit:More info

---

