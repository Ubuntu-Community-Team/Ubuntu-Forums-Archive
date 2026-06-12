---
title: "Installation error(&quot;Prepare disk space&quot; step)"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by vi0rulez on 2008-02-08
Although i have successfully partitioned my disk using gparted from the live cd (the new partition is recognized) once i try to install ubuntu and get to the "prepare disk space" step, i only get 2 available options : 1. Erase entire disk  2.Manually edit partition table
An option for "resizing the partition and use freed space" does not appear. Anyone knows whats wrong? thank you

---

### Post by Pumalite on 2008-02-08
If you use Vista, you have to allocate space from within Vista. If you have XP, use Gparted Live CD prior to the installation: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click in XP and choose 'resize from the menu. In the new space make 3 partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home
(or something proportionate)
Install Ubuntu, go Manual and use already made partitions.

---

### Post by vi0rulez on 2008-02-08
Im using XP, and i have made a single partition using gparted via the live cd. my question remains why the  "resizing the partition and use freed space" option does not appear.

---

### Post by Pumalite on 2008-02-08
Maybe you have a bad disk. Do md5sum on your iso, burn at 4x or less in good quality CD-R media and check for CD integrity before install. To make sure you have a clean hard drive, run sudo fdisk -lu from the Terminal with your Live CD.

---

### Post by vi0rulez on 2008-02-08
the disk seems ok. Can i use the option "manual edit partition table" ? would i need to create 3 separate partitions instead of 1? mount points?

---

### Post by Partyboi2 on 2008-02-08
With manual partitioning you will need to create /root (ext) partition and a /swap partition (2 times the size of your ram roughly) 
that would be enough to install ubuntu. But if you are wanting your /home (settings,docs, videos,pictures etc) on another partition then I suggest making one for /home (ext) as well. So something along the lines of what Pumalite suggested.

---

