---
title: "Grub did not install??"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by DoorGunner on 2010-09-03
Hi. I recently tried to install Ubuntu-netbook on to my usb drive. I did this using a USB pen drive. The installation went well. My only problem is i can not load windows or ubuntu up. I can get my pen drive to work still.... It appears that grub did not load anywere on the origional C:/ or USB drive. 

I have my bios set to accept a usb as a boot device. I was hoping to have it boot up on usb when it is plugged in and normal windows when the usb is not plugged in. 

any suggestions on how to fix this?

PS...havent used ubuntu in a while

---

### Post by oldfred on 2010-09-03
Just to see where grub installed and how your system is set up:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by DoorGunner on 2010-09-03
what is did was create a pendrive. I installed it to my USB drive. Were grub actually went is beyond me.

my fdisk -l says this

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       19458   156248920    7  HPFS/NTFS

Disk /dev/sdb: 8006 MB, 8006926336 bytes
16 heads, 32 sectors/track, 30544 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf67ff2c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30544     7819248    b  W95 FAT32

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00031d51

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30031   241217536   83  Linux
/dev/sdc2           30031       30402     2978817    5  Extended
/dev/sdc5           30031       30402     2978816   82  Linux swap / Solaris


note sda is my C drive where windows resides
sdb is my pen drive were i can currently get on a pen drive ubuntu
and sdc is my usb drive were ubuntu resides.

from what i gather both the my sda there is no real grub info there.

---

### Post by oldfred on 2010-09-03
The boot script will tell us what is where.

Generally grub just installs to sda as that is the boot drive. On the last install screen is an advanced button that lets you choose where to install grub. Just because you installed to a flash drive it still is an install to two drives.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Some settings from above link:
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

### Post by DoorGunner on 2010-09-04
Thank you ....that did the trick.... I should be able to do the rest...thanks

---

