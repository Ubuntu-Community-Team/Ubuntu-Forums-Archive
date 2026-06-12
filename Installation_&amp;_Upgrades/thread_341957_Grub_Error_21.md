---
title: "Grub Error 21"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by RobsterUK on 2007-01-19
I've been using Ubuntu for about 6 months, 6.06 then 6.10

Recently I bought a new hard drive and did a fresh install on the new drive with the existing ones still remaining in the machine. Of 3 drives I have one which has never had an OS on it and just used for storage. I want to remove that drive, but when I do I get Grub error 21 and I can't boot. If someone can give me any suggestions I would be grateful.

Grub menu.lst looks like this:

> 
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=bdf423d0-ae08-4d5d-ad6b-131057546a86 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.17-10-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=bdf423d0-ae08-4d5d-ad6b-131057546a86 ro single 
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=bdf423d0-ae08-4d5d-ad6b-131057546a86 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=bdf423d0-ae08-4d5d-ad6b-131057546a86 ro single 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-26-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=bdf423d0-ae08-4d5d-ad6b-131057546a86 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=bdf423d0-ae08-4d5d-ad6b-131057546a86 ro single 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, memtest86+ (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


Output of fdisk -l is:

> Disk /dev/hda: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2501    20089251    7  HPFS/NTFS
/dev/hda2            2502        3708     9695227+  83  Linux
/dev/hda3            3709        3737      232942+   5  Extended
/dev/hda5            3709        3737      232911   82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14593   117218241    b  W95 FAT32

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris


---

### Post by confused57 on 2007-01-19
Here's a description of grub error 21:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

I'm not sure, but I think what is happening is that when you remove the storage drive(hdc), your new drive on sda then is designated as hd1, instead of hd2.

What you can try is highlight the Ubuntu entry in your grub menu during bootup, press "e" for edit and change the root from (hd2,0) to (hd1,0) and try to boot with this change.
If it does, you'll need to make it more permanent by editing your /boot/grub/menu.lst.

---

### Post by RobsterUK on 2007-01-19
Thanks for the advice.

I actually solved this using more of a sledgehammer method. I removed all the drives apart from the one I wanted Ubuntu on, and did a clean install with a new partition using the whole drive. Works fine now :)

That also means I have now completely got rid of Windows...woohoo!

---

