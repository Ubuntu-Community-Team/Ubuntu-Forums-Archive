---
title: "Yet More SIL3114 Woes"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by Imaginary on 2007-08-26
Allow me to join in the chorus of crying newbies dying horrible, painful, SIL3114 RAID related deaths.

I decided to switch over from FC6 to Ubuntu.  Having no mothboard SATA support (SOYO Dragon KT333 Lite), I picked up a Syba SIL3114 SATA PCI card, and a new 320 GB SATA hard drive, figuring I'd set up a clean Ubuntu install on a shiny new drive, and then copy over settings and whatnot at my leisure.  The RAID card is connected only to the one drive, and is being told to treat it as just a single drive, with no RAID fancifications.

I tried using the SATA drive as my boot drive.  Grub couldn't start.  So I tried continuing to use my old IDE drive as the boot drive, and just grub across to the SATA drive.  Still no go.  When I try to boot to my Ubuntu installation, grub gives me "Error 21: Selected disk does not exist."  Same happens when I try to put together a grub boot disk.

As an added bonus, on this boot and this boot only, the SATA drive, which had been perfectly stable at /dev/sda, is now /dev/sde.

The drive is partioned as follows:
```
/dev/sde1          /boot
/dev/sde2          Extended partition
   /dev/sde5       swap
   /dev/sde6       /
   /dev/sde7       /data
```

My device.map is
```
(fd0)	/dev/fd0
(hd0)	/dev/hda
(hd1)	/dev/sda
```

And everything that's not commented out in my menu.lst is```

default=0
timeout=5
splashimage=(hd0,5)/grub/splash.xpm.gz
hiddenmenu
title Fedora Core (2.6.20-1.2948.fc6)
	root (hd0,5)
	kernel /vmlinuz-2.6.20-1.2948.fc6 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.20-1.2948.fc6.img
title Fedora Core (2.6.20-1.2944.fc6)
	root (hd0,5)
	kernel /vmlinuz-2.6.20-1.2944.fc6 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.20-1.2944.fc6.img
title Ubuntu, kernel 2.6.20-15-generic
	root (hd1,0)
	kernel /vmlinuz-2.6.20-15-generic root=UUID=b12bbd72-8cc9-468a-aa3b-f187dd26e7ef ro quiet splash
	initrd /initrd.img-2.6.20-15-generic
title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
	root (hd1,0)
	kernel /vmlinuz-2.6.20-15-generic root=UUID=b12bbd72-8cc9-468a-aa3b-f187dd26e7ef ro single
	initrd /initrd.img-2.6.20-15-generic

title Windows 2000
	rootnoverify (hd0,0)
	chainloader +1
```

Please, anyone, anything?  At the moment I flat out can not boot into my Ubuntu installation by any means I can find, and am hence stuck running a Fedora installation that, while flakey, at least comes up.  I could probably get around this by installing Ubuntu on the IDE drive, but is that really the only way?

---

### Post by Imaginary on 2007-08-30
One bump for old times' sake.

---

