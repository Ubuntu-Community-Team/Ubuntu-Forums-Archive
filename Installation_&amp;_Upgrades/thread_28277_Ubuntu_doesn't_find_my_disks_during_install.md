---
title: "Ubuntu doesn't find my disks during install"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by sp3tt on 2005-04-19
I have tried to install ubuntu today (really easy install btw), but when it gets to the part where I am supposed partition my drives, it can't find them.
My controller appears to be an "Intel 82801FB Ultra ATA Storage Controllers - 2652". That's what the windows device manager says.
I have resized the NTFS partition on the disk I wish to install ubuntu on (sdb) so that there is unpartitioned space (100GB). My disks are both SATA disks.
What is the problem, and how can I solve it?

---

### Post by alastair on 2005-04-19
There are already a lot of threads/people with the same problem - all SATA disks. Hardware moves faster than support sometimes. Do a search in the forums for "SATA" and have a look.

One thing, you could try playing with your BIOS and check the SATA support specified - perhaps try "legacy" or something. Make sure Windows still boots OK before trying Ubuntu though.

Good luck.

---

### Post by sp3tt on 2005-04-20
I did a search, and there were indeed many people having trouble with this, but I couldn't find any solutions.

---

### Post by sp3tt on 2005-04-21
Sorry for bumping, but I really need an answer. I tried to install in expert mode, and it said it could not load the ide modules.

---

### Post by sp3tt on 2005-04-21
Slight bump again, but anyway.
I tried to boot ubuntu from the live cd, it worked perfectly. I am typing this from ubuntu. I managed to mount my windows partition:
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdf: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       30515   245111706    7  HPFS/NTFS

Disk /dev/sdg: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       17362   139460233+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mkdir /mnt/win/
ubuntu@ubuntu:~$ sudo mount /dev/sdf1 /mnt/win/ -t ntfs -o umask=0222

I can even cd to /mnt/win/ and list the files, and show up in the file manager and I can read them... I still have no idea why ubuntu won't install.

---

