---
title: "LiveCD Feisty doesn`t admit to see partitions!"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by bartoldo on 2008-01-20
Uh, 
I have Ubuntu installed on HD, but, I had to change the motherboard (now it is ALiveNF4G-DVI with AMD Sempron(tm) 3200+ and dual channel DDR support) and i did expext problems with boot from HD, but, I didn`t expect these problems with LiveCD!
So, I have 2 HD`s, that are almost identical, the master is Maxtor 6Y080L0 and the slave Maxtor 6L080L0, both have 76 GB. The secondary IDE channel is empty, but, I have a SCSI adapter AHA-2940U/UW/D / AIC-7881U and a HD (IBM DXHS18Y) and a CD-Rom drive on it. Ubuntu has been installed on /dev/hda3, on that disk there is also another ext2fs partition as well as some swap and FAT partitions. On other 2 disks there are also several partitions, both Linux and Windows. Ubuntu is (should be) booted from Mandrake`s boot partition (Lilo) on another drive (/dev/hdb). If I try to boot it, I get busybox message "Can't access tty; job control turned off". OK, something alike has been expected. But, when I try to boot from a LiveCD, at first I was getting the same message, unless I booted with F6 or "driver CD" option (although I didn`t need to add any option, neither to insert another CD). Now. after I` ve dissabled the secondary (empty) IDE channel in BIOS, I`ve been able to boot stright (I don`t know if it was really corellated, maybe it was just a coincidence, however, it did happen now). But, the main problem is still here. And that is - Ubuntu doesn`t see any partitions on /dev/hda (on that disk only), so, I can`t mount /dev/hda3. Although gparted does see them, but, it sais "dumpe2fs: No such file or directory...". Also lshw sees them all and there doesn`t seem to be any difference about the way how it sees the partitions on the other disks. Except for one detail - it sais that disk is UDMA3 and /dev/hdb UDMA6, although both disks are set in BIOS to be autoidentified and all parameters are being identified as absolutely identical and I am not sure, but, I think, with the old motherboard it used to be UDMA5. Gnome hardware information about that disk sais also "storage.partitioning.scheme string none", while for the other disk it is "MBR". And the second detail - about the hdb it sais that the "block. minor" is 64 while that one (hda) would be - 0. But, that disk definitivelly *is* bootable! Maybe this Ubuntu`s "blindness" for the primary disk partitions could be something like "another side of the medale" of an error I have now in Windows9x (and DOS) - there the secondary disk is being seen - twice (and all partitions are being seen again, with another letter)! Knoppix LiveCD doesn`t exhibit any problem with partitions on any disk, but, I need the Ubuntu LiveCD to see them all, so I could be able to mount /dev/hda3 and fix the installation. BTW, for the moment, Mandrake is also unbootable, although Lilo works, I am trying first to fix Ubuntu.

---

### Post by bartoldo on 2008-01-20
Ops, I`ve just run discover and here they are! Now, I`ll see if I`ll be able to fixthe installation.

---

### Post by bartoldo on 2008-01-20
> **bartoldo said:**
> Ops, I`ve just run discover and here they are! Now, I`ll see if I`ll be able to fixthe installation.

... no, it sais /dev/hda3 is not a block device :(

---

### Post by bartoldo on 2008-01-20
That is, now I have /dev/hda1, /dev/hda2 etc., but, they haven`t populated /dev/disk

---

### Post by bartoldo on 2008-01-20
Ah, yes! That drive (/dev/hda), only that one, has been under logical volume management (EVMS, I think) in Linux, that is the difference! But, I don`t see how to do it from the LiveCD.

---

### Post by bartoldo on 2008-01-20
sudo blockdev --rereadpt /dev/hda and that`s it, I have them! Now I hope I`ll be able to fix the installation.

---

