---
title: "Another dual boot problem with Ubuntu and XP"
date: 2005-05-09
forum: Installation &amp; Upgrades
---

### Post by deburris on 2005-05-09
Hi, I would appreciate some assistance with a problem I'm having.  I was running XP on Thinkpad and decided to install Ubuntu 5.04.  I already had a small free partition so I chose to install Ubuntu to it.  The install went fine but when I rebooted, I get a Grub error 16 and my PC hangs.  I'm not very familiar with Grub.  I booted to a Knoppix Live CD so I can continue to poke around.  Here's some info that might be of help:

root@ttyp1[knoppix]# fdisk -l /dev/hda

Disk /dev/hda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4752    35925088+   7  HPFS/NTFS
/dev/hda2            4753        5146     2972025   83  Linux
/dev/hda3            5146        5168      168682+   5  Extended
/dev/hda5            5146        5168      168651   82  Linux swap

and here's the Grub menu.lst file:

title  Ubuntu, kernel 2.6.10-5-386 
root  (hd0,1)
kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd  /boot/initrd.img-2.6.10-5-386
savedefault
boot

title  Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root  (hd0,1)
kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd  /boot/initrd.img-2.6.10-5-386
savedefault
boot

title  Ubuntu, kernel memtest86+ 
root  (hd0,1)
kernel  /boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title  Microsoft Windows XP Professional
root  (hd0,0)
savedefault
makeactive
chainloader +1

Anything else that might assist in debugging the problem?

Thanks in advance!

Dean

---

### Post by defkewl on 2005-05-09
Could you please also paste /etc/fstab here.

---

### Post by deburris on 2005-05-09
Sure.  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by spd106 on 2005-05-09
Hi, check that /boot/grub/device.map contains the line

(hd0)   /dev/hda

aslo try doing 
```
$sudo update-grub
```
from the command line to automatically configure the menu.lst then check for changes. i suggest you back it up first though, ie
  
```
$sudo cp -i /boot/grub/menu.lst /boot/grub/menu.lst.old
```

Hope this helps

---

### Post by deburris on 2005-05-09
Thanks.  Unfortunately, didn't help.  The file already had the line and grub-update failed.

---

### Post by spd106 on 2005-05-10
Hi, according to the grub website an error 16 indicates possible file system corruption, so it might be best to reinstall ubuntu.

Also, have you tried running fsck?
 
NB You have to make sure the file system is not mounted first.

Good luck

---

