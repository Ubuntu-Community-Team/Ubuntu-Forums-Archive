---
title: "Weird stuff happening on my Acer C720 Mint laptop"
date: 2016-04-16
forum: MINT
---

### Post by Watchamacolite on 2016-04-16
I'm in a bit of a rut here.

I went to get some warm clothing and when I came back, my computer had shut off. Weird but maybe it was updating, who knows. Booting it back up (with the legacy boot on a chromebook; i can select which hard drive to boot into) resulted in an errorless message:

```

SeaBIOS (version xxx)

Press ESC for boot menu.

Select boot device:

1. AHCI/0: PS3109S9 ATA-7 Hard-Disk (20 MiBytes)

Booting from Hard Disk . . .
Boot failed: not a bootable disk

Booting from Floppy . . .
Boot failed: could not read the boot disk

No bootable device.

```

With my limited knowledge of the subject I figured that a ninja update had wiped the boot file from it, or the disk was unmounted, whatever. Something that seems easily fixable (and this might still be the case). I made a live USB and did an integrity and memcheck, both of which turned out just fine. Booting into the USB and i run sudo fdisk -l to get the different drives, and my /dev/sda (my 128GB SSD hard drive) displays a couple notable things.

Firstly, my SSD has shrunken from 128GB to 20MB according to fdisk -l, and it also gives me "Disk /dev/sda doesn't contain a valid partition table".

```

Disk /dev/sda: 20MB, 20972032 bytes
255 heads, 63 sectors/track, 2 cylinders, total 40961 sectors
 . . .
Disk identifier: 0x00001000

```

and my live usb being right under it with correct stats, the most notable difference being the size, number of cylinders (1956), sectors, and disk ID. I have no idea what to do at this point, is my data still recoverable? Even if I have to repartition or format my drive, is there any way I can get the data off of it first? Or even better, can I just make it all magically work again?

Any help would be much appreciated!

Edit: After trying to access the PSE109S9 (the other optton being just "file system", apparently 140 TB large [?]) from the live USB, it says that it isn't mounted, but I don't want to touch anything without knowing what I'm doing first. Ill wait for input.

---

### Post by deadflowr on 2016-04-16
Thread moved to the **MINT** sub-forum

---

### Post by Watchamacolite on 2016-04-18
I'm still having a problem if anyone would be so kind as to point me in the right direction. At this point I think it might need replacing but I'm not experienced enough to know for sure.

---

### Post by Watchamacolite on 2016-04-18
Okay so I've solved this myself

As it turns out my SSD has completely and utterly failed and is pretty dead. There was no surge or anything (surge protector) so I'm guessing it just crapped out.

Some info,
- SSD is about 7 months old at this point, expected at least 1.5+ years, will be getting a replacement from the dealer
- [SIZE=2]MyDigitalSSD SC2 Super Cache 2 42mm SATA III 6G M.2 NGFF M2 2242 SSD Solid State Drive (128GB) bought from amazon for $59.99, 3 year warrenty
- Installed manually in an Acer C720 laptop
[/SIZE]

---

