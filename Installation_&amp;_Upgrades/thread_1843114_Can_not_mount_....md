---
title: "Can not mount ..."
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by Vapetek on 2011-09-12
Hey guys, 

having a few problems getting Ubuntu 11.04 installed on my desktop. Here is the exact error it is giving me,

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error

Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

Anyone know what to make of this? The hard drive is a WD Caviar Blue 320GB [MDL: WD3200AAJB - 00J3A0]. The CD-ROM is a Super Multi DVD Rewriter. Going off that error code it gave me, I'm guessing it has something to do with the CD-ROM but the drive is un-partitioned/untouched at this point.

Thanks for any help!

---

### Post by pjd99 on 2011-09-12
Looks like it could be a bad burn. That output has nothing to do with the HDD.

I'd re-burn the disc with a CRC/MD5 checksum and try again.

---

### Post by Pariah819 on 2011-09-12
So I'm guessing your trying to boot off of a CD to format and install Ubuntu on your hard drive?  I would recommend making sure the CD burned correctly, there should a menu option to check the CD image checksum at the initial boot menu of the CD.  I've read many posts where people suggest writing the CD at the slowest possible speed to prevent errors during the burn.

---

### Post by Vapetek on 2011-09-12
> **Pariah819 said:**
> So I'm guessing your trying to boot off of a CD to format and install Ubuntu on your hard drive?  I would recommend making sure the CD burned correctly, there should a menu option to check the CD image checksum at the initial boot menu of the CD.  I've read many posts where people suggest writing the CD at the slowest possible speed to prevent errors during the burn.


Just installed Ubuntu on this laptop with the same CD. Pretty sure this is a BIOS problem with my CD-ROM. Thanks anyways guys

---

