---
title: "Grub Error 15"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by varean on 2006-10-09
I found some old unused space on my HD recently so I decided to hop into my Ubuntu LiveCD and resize my disk so I get an extra 30gigs on my Ubuntu drive(/dev/sda).  I resize it then I go toboot into ubuntu but when it tries to load grub, it says "grub 1.5 initializing" and then it says "Error 15" and it freezes.  I am unable to even go into the grub menu.  I have it set so I boot from hd0,1, which is my /dev/sda1 partition, which is what I need for boot.  However, when I edit the menu.lst in the live cd, I am unable to run grub-install because it says device not found or not valid block device.  I tried chrooting and doing it, mounting the drive, unmounting it, etc, So I really don't know where to go from here.  Any help is appreciated, thanks.

---

### Post by K0LO on 2006-10-09
> I have it set so I boot from hd0,1, which is my /dev/sda1 partition
In GRUB lingo, sda1 is (hd0,0) **not** (hd0,1). Could this be the problem?

GRUB Error 15 is > 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

---

### Post by varean on 2006-10-09
> **K0LO said:**
> In GRUB lingo, sda1 is (hd0,0) **not** (hd0,1). Could this be the problem?

GRUB Error 15 is

The problem is that I cannot edit the menu.lst.  I am unable to run grub-install on my HD, so all the changes I make wont take effect.

---

### Post by K0LO on 2006-10-09
Using your Ubuntu LiveCD to boot up, get to a console and then type:```
sudo fdisk -l
```to print out the partition structure of your disk. Make sure that you know the partition numbers for each partition of interest to Ubuntu. If you post the output here, I'll take a look and try to help out.

Next type:```
sudo grub
``` to get to a GRUB prompt. You can then try the following to locate your GRUB stage 1.5 files:```
find /boot/grub/stage1
```GRUB should return the partition number [like (hd0,1), for example] of its stage 1 file. If you are then sure of their location you could install GRUB to the master boot record of your drive by following the instructions in the GRUB manual [here.](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively)

When you resized your disk did you create any new partitions? And if so, could you describe how you did the resize?

---

### Post by varean on 2006-10-09
Still no luck.  Here is fdisk -l:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19269   154778211   83  Linux
/dev/sda3           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14592   117210208+   7  HPFS/NTFS
```

I chroot into /mnt, where /dev/sda is mounted and I check my menu.lst, which shows that everything is in order:
```
cat menu.lst
title           Ubuntu, kernel 2.6.15-27-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title           Microsoft Windows 2000 Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Here is my error when running grub-install /dev/sda
```
root@ubuntu:/boot/grub# grub-install /dev/sda
/dev/sda: Not found or not a block device.

```

And when in the grub terminal:
```
grub> install (hd1)

Error 21: Selected disk does not exist

grub> setup (hd1)

Error 12: Invalid device requested

grub> setup (hd1,0)

Error 12: Invalid device requested
```

Ideas?

---

### Post by K0LO on 2006-10-09
Sorry, I have to run (teacher; am giving an exam tonight!)

Did you switch the boot order of your hard disks in the BIOS? They look reversed from your GRUB menu.lst file.

---

### Post by varean on 2006-10-09
Y'know, I think thats that problem!  Ill fix it and give an update

EDIT:  I tried changing the order, but when I set it so that my windows HD is 1st boot device, then it automatically boots from there.  If my linux HD is the 1st, I get the error.

---

### Post by K0LO on 2006-10-09
Then if you want your Linux disk (sda) to be the boot device you need to install GRUB to (hd0), not (hd1) as follows:
```
grub> setup (hd0)
```

Also, the references in the menu.lst file need to be swapped. All references to (hd1,0) need to be (hd0,0). The reference to (hd0,0) needs to be (hd1,0)as follows:
```
title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:

root <<--- This needs to be deleted


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title           Microsoft Windows 2000 Professional
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader     +1
```

**Note the stray line with "root" needs to be deleted also. It will cause a GRUB error. And for starting Windows you need to reference the partition as "rootnoverify" instead of "root". Since GRUB doesn't understand the NTFS filesystem, using "root" here will also cause a GRUB error.

---

### Post by varean on 2006-10-09
Is there a way then I could install it on my Ubuntu HD?  I really don't want to mess with my Window's boot sector on its HD.

---

### Post by K0LO on 2006-10-09
GRUB numbers disks and partitions starting with zero. So the first hard disk is (hd0). That's sda, your Linux disk. The second hard disk is (hd1). That's sdc, your Windows XP hard disk.

So the procedure that I outlined in my previous post will install GRUB to the master boot record of your Ubuntu hard disk, sda, or (hd0).

If you want to be absolutely certain that you won't accidentally change the Windows XP disk's master boot record, turn off the PC and disconnect the Windows XP hard disk before making any changes. Then if the Linux disk is the only hard drive in the PC, that's the only disk that GRUB can write to.

---

### Post by varean on 2006-10-13
I still cant get it to work.  I cant install to hdc or sda no matter what I try.  I change the boot order, I enter the grub terminal and i cant install to any disk, I get the same invalid device requested no matter what I do.

---

