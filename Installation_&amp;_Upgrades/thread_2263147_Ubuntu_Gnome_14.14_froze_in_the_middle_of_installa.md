---
title: "Ubuntu Gnome 14.14 froze in the middle of installation"
date: 2015-01-29
forum: Installation &amp; Upgrades
---

### Post by archp2009 on 2015-01-29
I have a very complex multiboot setup.  I just attempted to add one more flavor of Ubuntu but I was unable to type a user name etc when I got to this point.  I pressed back and was still unable to get keyboard to work or to be detected.  I have never had this happen before.  I am leaving my computer turned on in this state as neither back or continue will respond nor keyboard. I am using a standard ps3 keyboard.  I tried a cheap usb keyboard as well. What can I do now?

---

### Post by archp2009 on 2015-01-29
I hit reset went back into live cd and ran gparted.  It said overlapping partitions.  Didn't see that before. I deleted the new partition that was created in the first half of the attempted installation of Gnome 14.10.    Grub was not overwritten so no problems getting back in to the other stuff. How do I detect/fix the overlapping partition. With regard to the keyboard issue the keyboard plug may have been half way out.

---

### Post by archp2009 on 2015-01-30
arch@arch-System-Product-Name:~ > sudo fdisk -lu
[sudo] password for arch: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5d7d47e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   287547434   143773686    7  HPFS/NTFS/exFAT
/dev/sda2       287547435   532876049   122664307+   7  HPFS/NTFS/exFAT
/dev/sda3       532876050   778204664   122664307+   7  HPFS/NTFS/exFAT
/dev/sda4       778204666  1953520064   587657699+   5  Extended
/dev/sda5       778204729  1953520064   587657668    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc4102f2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *   203929110   469740599   132905745    7  HPFS/NTFS/exFAT
/dev/sdb2       469756658   687919364   109081353+   7  HPFS/NTFS/exFAT
/dev/sdb3       687919428   893358584   102719578+   7  HPFS/NTFS/exFAT
/dev/sdb4              65  1250258624   625129280    f  W95 Ext'd (LBA)
/dev/sdb5             128   203929109   101964491    7  HPFS/NTFS/exFAT
/dev/sdb6       893374708  1250258624   178441958+   7  HPFS/NTFS/exFAT

Partition table entries are not in disk order

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b7fa170

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    29296969    14647461   83  Linux
/dev/sdc2        29298686   625141759   297921537    f  W95 Ext'd (LBA)
/dev/sdc5        29298688    39452671     5076992   82  Linux swap / Solaris
/dev/sdc6        39454720    82075647    21310464   83  Linux
/dev/sdc7        82077696   123844607    20883456   83  Linux
/dev/sdc8       123846656   154687487    15420416   83  Linux
/dev/sdc9       154689536   185438207    15374336   83  Linux
/dev/sdc10      185440256   218402815    16481280   83  Linux
/dev/sdc11      218404864   259851374    20723255+  83  Linux
/dev/sdc12      259852288   290758655    15453184   83  Linux
/dev/sdc13      290760704   331900927    20570112   83  Linux
/dev/sdc14      331902976   366860287    17478656   83  Linux
/dev/sdc15      402123072   625141759   111509344    7  HPFS/NTFS/exFAT
arch@arch-System-Product-Name:~ >

---

### Post by archp2009 on 2015-01-30
sdc5 (swap) appears to have almost the same start point as sdc2.  Ubuntu Gnome chose and formatted this swap partition automatically during the partial installation.  I did not manually choose any swap partition because I know there already was one there.  I'm not immediately sure what sdc2 was previously if it was not a swap partition.

---

### Post by archp2009 on 2015-01-30
I just had a look at my grub in Grub Customizer and it shows that my 10 linux distros are installed on sdc1,6,7,8,9,10,11,12, 13, and 15. I don't know why no entry is shown in the grub menu for sdc14 and I don't know why sdc2 and sdc5 were created nor why sdc3 and sdc4 are not enumerated by fdisk.

---

### Post by archp2009 on 2015-01-31
I ignored the overlapping swap partition and reinstalled Ubuntu Gnome 14.10 without incident.  I don't know if the overlapping partition will cause problems down the road or not.

---

