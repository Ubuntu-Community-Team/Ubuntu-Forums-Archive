---
title: "Install GRUB after already install Ubuntu"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by carrie.peary on 2008-09-07
Ok, I've installed Ubuntu before on an partitioned external HDD and am trying again to do so. I'm following the same tutorial from this site as before, but one that that I'm stuck on is that once it gets to 94%, it says 'grub-install /dev/sdb' failed. It's the right drive (sdb) but can't seem to install it. I've checked the CD for defects but comes back clean. I've also tried to make it install to a random partition/free space I've created for it (ie. /dev/sdb5) with also no luck.

So I now have Ubuntu installed, but since I did not check the "Install GRUB" box can't access it since I do not have GRUB to recognize it atm. 

How can I install GRUB now, after already having installed linux, onto my external hard drive? I've searched for tut's but they only seem to cover how to reinstall...not just install.

Thanks!

Oh, and since someone will ask, here's some specs:
WD Passport External HDD, 250GB, Ubuntu using 10GB
MacBook running Leopard

---

### Post by caljohnsmith on 2008-09-07
Having the install fail at 94% with a Grub install problem is a known bug that you can get around by formatting Ubuntu's partition to be "ext2" instead of "ext3". If you are then able to successfully install, you can upgrade your ext2 file system to ext3 with the following command in Ubuntu:
```
sudo tune2fs -j /dev/sdXY
```
where sdXY is your Ubuntu partition.

---

### Post by Sef on 2008-09-07
Instal GRUB with [Super GRUB Disk]("http://www.supergrubdisk.org/").

---

### Post by carrie.peary on 2008-09-07
But how would I go about paritioning it for ext2 and not ext3? I'm doing the "Manual free space" option and letting it do the rest....

---

### Post by caljohnsmith on 2008-09-07
> **carrie.peary said:**
> But how would I go about paritioning it for ext2 and not ext3? I'm doing the "Manual free space" option and letting it do the rest....
It's been so long since I've done an install from the CD that I don't remember if you can format the partitions during the installation, but if you can't find that option, then before the install, hit Alt + F2, and type:
```
gksudo gparted
```
That opens the partition editor, just select the Ubuntu partition, right-click and set format to "ext2". Then hit "apply". If you run into problems let us know, but that should work.

---

