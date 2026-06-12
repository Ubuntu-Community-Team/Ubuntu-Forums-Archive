---
title: "[SOLVED] Ubuntu on two drives one now missing vers 24-22"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by Tom Atkins on 2008-11-28
I installed HH from the DVD several months ago on my b drive (Suse 10.0 was on a) and after using it I decided to migrate everything to HH. I did that and then installed HH on the a drive intending to use it for Upgrades and other things. The install went well and it recognized my b drive as another system and added all the versions of Linux I had had in GRUB. Today I ran the updates to 24-22 on both systems. The GRUB for the original install did not update to 24-22 while the new on did add it to its part but not the original. How do I update GRUB for my original install? Here is some info on my system:
```

tommy3@tommy3-desktop:~$ sudo fdisk -lu
[sudo] password for tommy3: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cd3b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   150288074    75144006   83  Linux
/dev/sda2       150288075   156296384     3004155    5  Extended
/dev/sda5       150288138   156296384     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000abcfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   150288074    75144006   83  Linux
/dev/sdb2       150288075   156296384     3004155    5  Extended
/dev/sdb5       150288138   156296384     3004123+  82  Linux swap / Solaris

```

```

grub> find /boot/grub/stage1
 (hd0,0)
 (hd1,0)

grub> 


```
```

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=c281befe-c845-4fe8-9c49-1ce25e2f9f57 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=c281befe-c845-4fe8-9c49-1ce25e2f9f57 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c281befe-c845-4fe8-9c49-1ce25e2f9f57 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c281befe-c845-4fe8-9c49-1ce25e2f9f57 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c281befe-c845-4fe8-9c49-1ce25e2f9f57 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c281befe-c845-4fe8-9c49-1ce25e2f9f57 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```
The above were run from my new system on the A drive.
I have both the Unbutu DVD and a Super GRUB CD.

Thanks for any help

---

### Post by cariboo on 2008-11-28
I have Intrepid on the second half of my primary IDE drive and Jaunty on my first Sata drive, the computer boots from grub on the sata drive. When the kernel is updatedin Intrepid, I just paste the appropriate section in to grub on the sata drive. There is a way to chainload the kernel from another partition, but it's is one of those projects I haven't got around to yet.

Jim

---

### Post by Tom Atkins on 2008-11-29
Thanks a lot for your help. It worked perfectly.

---

### Post by markbuntu on 2008-11-29
chainloading is dirt simple, 3 lines at the end of menu.lst and one is a comment line. you do it like this;


# title Chainload 8.04 amd64
root       (hd1)
chainloader  +1

#title chainload mandriva
root          (hd2)
chainloader   +1


#title chainload Intrepid
root         (hd3,0)
chainloader  +1

Each one of these has its own grub that gets started by the chainloader, no need to change anything until you change the boot partition.

---

