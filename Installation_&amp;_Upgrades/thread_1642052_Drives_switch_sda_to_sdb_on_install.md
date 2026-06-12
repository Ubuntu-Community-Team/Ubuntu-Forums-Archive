---
title: "Drives switch sda to sdb on install"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by jwillo38 on 2010-12-09
Hello,all.  I'm trying to install 10.10  to my home desktop that has Win xp.  I have one ide hd with only windos on it and I have a sata hd partitioned logically for linux.  The sata controller is a via chip on an old Abit mobo.  The live cd works great but when I run the install and get to the partitioning, my sata disk becomes sda instead of sdb.  From the live cd, gparted shows the sata as sdb.  From live, "cat /proc/partitions" shows the sata disk as sdb.  But during install gparted shows it as sda.  The install will go on the correct drive, but I'm not sure where to put grub2.  On another distro install, I left it at mbr, and it went to the sata mbr. Should I just install grub to the ide disk which will become my "sda" at boot?  Will grub find ubuntu on the sata disk, which will become sdb?

---

### Post by ronparent on 2010-12-09
Welcome to the forum.

That last is probably what you want. I take it that you want the grub on the disk that is set to boot 1st in bios.

What the disks are indicated during install will often shuffle when the system is actually booted. Since the system defaults to booting by uuid the sdx designation bears no special relationship to the boot configuration. Post again if you run into trouble.

---

