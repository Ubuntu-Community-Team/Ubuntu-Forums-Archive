---
title: "i have boot menu but cannot boot into xp or ubuntu"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by tuxulin on 2008-09-16
im having problems with one of my machine
here is the situation at hand.


i have 2 hard disks the one ide and sata.
both are visible in their respective BIOS

i installed xp on the ide, during installation i created another
partition for ubuntu on the same disk. (raw partition).

XP installation and ubuntu installed perfect however
when i rebooted only xp was working (no ubuntu boot menu)

i then reinstalled grub and got the menu working but now
when i reboot i first get a
error 15 file not found then on pressing enter i then get a
error 18 Selected cylinder exceeds maximum supported by BIOS.

so i currently cannot boot into either ubuntu or XP.

hare are some detials

disks and their labels
> 
Disk /dev/sda: 81.9 GB ntfs win xp and ubuntu
/dev/sda1 Windows NTFS
/dev/sda5 Linux ext3 /
/dev/sda6 WorkBin ext3
Quote:
Disk /dev/sdb: 251.0 GB
/dev/sdb3 /home
/dev/sdb5 /archives
/dev/sdb1 /free space


ubuntu@ubuntu:~$ sudo fdisk -l
> 
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf46af46a

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1912 15358108+ 7 HPFS/NTFS
/dev/sda2 1913 9964 64677690 f W95 Ext'd (LBA)
/dev/sda5 1913 4462 20482843+ 83 Linux
/dev/sda6 4463 9964 44194783+ 83 Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2be35099

Device Boot Start End Blocks Id System
/dev/sdb1 * 17766 27965 81931500 5 Extended
/dev/sdb2 1 373 2996091 82 Linux swap / Solaris
/dev/sdb3 374 17765 139701240 83 Linux
/dev/sdb5 17766 27965 81931468+ 83 Linux

Partition table entries are not in disk order


menu.lst
> 
title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd1,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=1283a46d-77d9-474a-b311-a562e80217ee ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd1,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=1283a46d-77d9-474a-b311-a562e80217ee ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd1,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


please help and thanks you
Tuxulin

---

### Post by caljohnsmith on 2008-09-16
OK, try rebooting, and when you get the Grub menu, select Ubuntu, hit "e" to edit, select the line that says "root (hd1,4)", press "e" to edit it, change it to "root (hd0,4)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes. If not, please clarify which HDD you are booting from. Also note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent if it works. Let me know how it goes, and we can go from there.

---

### Post by tuxulin on 2008-09-16
@ caljohnsmith yes that did the trick all is firing again as it should

you are the Topman :)

Tuxulin

---

### Post by caljohnsmith on 2008-09-16
Glad it worked. :) One last thought though, since Ubuntu is on (hd0), so is your Windows. So if you want to get Windows to boot, I believe you'll also need to change its menu.lst entry to:
```
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```
Maybe you've all ready made the change, but in case you haven't... :)

---

