---
title: "Dual-booting Ubuntu and Pardus with GRUB2...Pardus no show?"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by Ibn Ali al-Turki on 2011-01-23
Hello all,

I have Ubuntu 10.10 installed and used to dual-boot Fedora, but I replaced Fedora with Pardus.

After the install, I went into ubuntu, and did a sudo update-grub. It detected my Pardus 2011 install there. When I rebooted, it did not show up in my grub2 menu however. I went back to Ubuntu and did it again...then checked the grub.cfg, and it is not there. I have read that Pardus uses a grub legacy.

How can I get Pardus into my grub2 menu?

Thanks!

sudo fdisk -l
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9b3496e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15197   122067968   83  Linux
/dev/sda2           36394       60802   196059757    5  Extended
/dev/sda3           15197       30394   122067968   83  Linux
/dev/sda5           36394       59434   185075308    7  HPFS/NTFS
/dev/sda6           59434       60802    10983424   82  Linux swap / Solaris

Partition table entries are not in disk order


and

update-grub
> Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Pardus 2011 (2011) on /dev/sda3


Yet after this, I go to grub.cfg, and Pardus is not there.

---

### Post by mikewhatever on 2011-01-24
You could try adding a custom entry for Pardus to grub2, or use Pardus to manage boot the two OSs. The second option seems to be easier.
[http://www.dedoimedo.com/computers/pardus.html](http://www.dedoimedo.com/computers/pardus.html)

---

### Post by Ibn Ali al-Turki on 2011-02-07
The solution for me was to install Pardus with it's own bootloader on it's own partition.  Then just do sudo update-grub.

That's all. :)

---

