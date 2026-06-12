---
title: "[SOLVED] Error Loading Operating SYstem"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by Boyohazard on 2008-03-19
Hi all
I'm trying to install Ubuntu on my home desktop, (seemed to have lost my Win XP documents along the way D'OH!) but when I try to boot up it says Error Loading Operating System.

I've tried a couple of re-installs using different live cds but to no avail.

menu.lst:
```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4760d01d-1cbb-425c-b1d6-114a08b1d477 ro quiet splash noapic
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4760d01d-1cbb-425c-b1d6-114a08b1d477 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

fdisk -l:
```
Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86296005

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33943393

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris
```

fstab:
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```
I feel like I am missing something obvious please point it out to me :-D

---

### Post by Pumalite on 2008-03-19
Use Super Grub to boot either OS: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Beyond that; you seem to have the old IDE+SATA mix problem. Take a look at these links:
[http://ubuntuforums.org/showthread.php?t=46003](http://ubuntuforums.org/showthread.php?t=46003)

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by Boyohazard on 2008-03-19
Thanks Pumalite

I'm going to have to download Super Grub Loader on another machine I cannot use this one to burn cd's whilst using the Live CD

I'll reply with my results when it's done

---

### Post by Boyohazard on 2008-03-19
OK I carried on fiddling while I wait to get to a computer to download SGL and I changed the boot options from SATA to IDE and it fixed my problem :)

Since the IDE drive is old and on its way out how do I change my setup to successfully boot from the SATA instead please?

---

### Post by Pumalite on 2008-03-19
In that case I would install on the SATA both systems (making it master) and keep the IDE for storage /and/or a /home partition for Ubuntu.

---

