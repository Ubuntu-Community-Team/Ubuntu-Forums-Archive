---
title: "Can't install. Odd behavior occurs."
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by Gidgidonihah on 2008-08-15
I tried to install Ubuntu today and failed miserably.

**FIrst the computer specs straight from my Newegg history.**

```
Intel Core 2 Quad Q6600 Kentsfield 2.4GHz LGA 775 Quad-Core Processor Model BX80562Q6600
DFI INFINITY P965 DARK
eVGA Nvidia 7800gt 256
mushkin 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800
Seagate Barracuda 7200.10 ST3500630AS 500GB 7200 RPM SATA 3.0Gb/s Hard Drive
Thermaltake Purepower W0129RU 600 W ATX12V Power Supply
Generic DVD drive
Soundblaster Audigy
```

**Okay, now the problem.**

I installed XP for gaming and wanted to install Ubuntu for everything else. I partitioned the HDD 200 for xp, 200 for storage and the last 100 left for ubuntu.

When I booted to the CD everything appears fine. I chose english and then chose 'install'. The orange bar started moving but stopped about 90% of the way. Nothing happened after that, so I restarted and chose 'load without changing files'. After the loading finished (orange bar full) the main monitor (I have 2) went blue and the secondary flashed green and a mouse pointer was in the middle of the blue screen. The mouse wouldn't move and nothing else happened.
I tried one more time and this time the Ubuntu desktop appeared on the main screen though I couldn't see the menu bars. A dialog box appeared with a garbled image and I couldn't do anything else.

I've never had this problem with ubuntu before. But I'm thinking hardware. When I tried installing Windows Server 2008 I did have a similar problem. The installer would freeze at random times, usually while 'expanding files'. Same thing happened with vista when I tried just to see if it would install. So basically I can't install anything but XP.

When I was trying to find the problem while installing Win Server 2008 I swapped out all the hardware/cables except the PSU, CPU and Mobo. Maybe the GPU too, I can't remember. So the problem wasn't with the hard drive or dvd drive.

Additionally, sometimes when  I start the computer the bios shows the CPU and does nothing else. I have to cut power to the PSU and restart then it will boot fine.

The hardware was all bought back in July 07. Not sure where to go with this one.

---

### Post by spiderbatdad on 2008-08-15
I've seen other using the boot options (F6) at startup. Delete quiet splash-- and add all_generic_ide, then hit enter. If this works, you will need to edit /boot/grub/menu.lst to make the change permanent.

---

### Post by Gidgidonihah on 2008-08-15
Tried what you said. 

Froze after:
```

[88.584518] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[88.584582] sd 6:0:0:0: Attached scsi generic sg2 type 0

```

---

### Post by spiderbatdad on 2008-08-15
Not sure...kernel trying to cope with hardware? You may have to wait 5-6 minutes. Obviously some other parameters might work better...as obtained via dmesg...but that would require a complete boot.

---

### Post by Gidgidonihah on 2008-08-15
Naturally I waited to make sure nothing was happening.
I'm at a loss.

---

