---
title: "grub error 21"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by _pitch on 2008-01-24
Hi,

With risk of repeating I'd like to tell you about my problem and how I solved it.

I got the GRUB error 21 message after I've installed Ubuntu on my work (XP) laptop on external usb disk and with the disk unatached.
As I found out the problem consist in that the Ubuntu installer mess up your MasterBootRecord, mbr.
If you want to boot  your NT/2000/XP and maybe Vista to boot without your usb drive attached you have to do the following...:

Make your usb-drive boot before your internal harddrive in BIOS.

Make your linux partition bootable with your favourite fdisk-tool...I prefer cfdisk in linux. I don't know if this is really necessary but it won't hurt...
While you're in linux with your external drive edit your /boot/grub/menu.lst to look something like this in the Windows part:
```
title           Microsoft Windows XP Pro
map             (hd0) (hd1)
map             (hd1) (hd0)
rootnoverify    (hd1)
chainloader     +1

```

And install both part of grub into your external drive (/dev/sdb1 in my case) by running the command:
```
grub-install /dev/sdb1
```

Boot on your NT/2000/XP CD and chose repair option and run ```
fdisk /mbr
``` or any other tool that will fix your MasterBootRecord.

Reboot and you hopefully got it working now.

---

