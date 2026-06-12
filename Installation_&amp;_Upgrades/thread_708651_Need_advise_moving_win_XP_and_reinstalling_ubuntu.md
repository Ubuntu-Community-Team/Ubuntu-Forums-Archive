---
title: "Need advise moving win XP and reinstalling ubuntu"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2008-02-26
Hi. I got an old box from my dad that wasthe exact same model as mine so I swaped out his ram and also a 80Gig hard drive into my old box. 
 
 Anyways there seems to be a few problems as it takes a very long time to boot up so I want to do a reinstall of Ubuntu.
 
 My original box had a newer 120G WD hard drive and a old 40G drive. I swaped out the old 40 gig and slapped in the 80 gig I got from my dad. The 120G dive has been set up for a lon time with three partitions XP, a Fat32 document drive that I shared  between xp and Ubuunu. The 80G was formated as ext3 and is being used as the documents drive.
 
 I have to do something as the partions on the 120 are to small other than for XP 37G each.
 
 Now I am thinking of going puse Ubuntu but am planning to install the Ubuntu on the 80G drive and formating the hole 120G as a Home pation mount.
 
 So now this brings me to the point of having the 120 mounted as home and the 80G as the ubuntu install I really will not need 80 gigs for Ubuntu. I was wondering if it possible to make a small ntfs partition on the 80G drive and swap all the files from the XP partion and fix up grub after reinstalling Ubuntu. The XP is a purches xp home upgrade so having it sit on a small partition as a backup would be ok and seeing as I bought it along time ago guess I should use it.
 
 Anyways I really do not want to reinstall xp and do all the upgrades so if its too much to do will go with a pure Ubuntu install.

---

### Post by Pumalite on 2008-02-26
Boot a Live CD and from the Terminal, post:
sudo fdisk -lu

---

### Post by Omnios on 2008-02-26
> **Pumalite said:**
> Boot a Live CD and from the Terminal, post:
sudo fdisk -lu
 
Hi here is the output of fdisk ran it from Ubuntu
 
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0f0f0f0
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    77657599    38828768+   7  HPFS/NTFS
/dev/sda2        77657600   156039344    39190872+   7  HPFS/NTFS
/dev/sda3       156039345   234436544    39198600   83  Linux
 
Disk /dev/sdb: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders, total 156355584 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd75bd75
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   154240064    77120001   83  Linux
/dev/sdb3       154240065   156344579     1052257+  82  Linux swap / Solaris
 
 

```

---

### Post by Pumalite on 2008-02-26
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Shrink XP partition. Format the new space ext3. Make one large partition of the drive you want to make home and give it a mount point: /home. Then Install Ubuntu and use the prepared partitions by going Manual

---

### Post by Omnios on 2008-02-27
> **Pumalite said:**
> Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Shrink XP partition. Format the new space ext3. Make one large partition of the drive you want to make home and give it a mount point: /home. Then Install Ubuntu and use the prepared partitions by going Manual
 
 Anyways went with a reinstall and got everything set up all nice. Thanks for the link for the gparted live cd could not have done it without it. Now I have a nice 120G home directory,,, Sweeet.

---

### Post by Pumalite on 2008-02-28
You are welcome. Good luck.

---

