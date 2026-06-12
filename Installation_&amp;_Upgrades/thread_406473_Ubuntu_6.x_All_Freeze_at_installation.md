---
title: "Ubuntu 6.x All Freeze at installation"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by Geekkit on 2007-04-10
I'm not sure what's wrong here but I cannot, for the life of me, install Ubuntu on my PC. My specs are as follows:

- P4, 3 GHz, 512 MB RAM
- Asus P4S800D-X with RAID BIOS Setting Utility v1.05_964
- 2 hard disk drives: WDC WD400BB-34DEA0 (80 GB), WDC WD800JB-00JJA0 (40 GB)
- NVIDIA GeForce4 Ti 4200 AGP 8x
- DVD Rewritable disks: HL-DT-ST DVDRAM GSA-41638 (LG), HP DVD Writer 200j (HP)

I've tried 6.10 (yes, the checksum is correct, after downloading), and the 6.06 version that came in that cute little sleeve showing the five people all holding hands showing how much fun Ubuntu is (i.e., the mass produced disk) does the same thing. IOW, Neither work. :( 

What happens:
---------------------
1.) BIOS completes
2.) Ubuntu screen kicks in. If I choose to boot in safe mode or install, Ubuntu gets as far as this (displays):

[FONT="Fixedsys"]Loading /casper/vmlinuz...................
Loading /casper/initrd.gz...................[/FONT]

Then hangs. If I choose memory test, that seems to work (although it's exhaustive so I didn't wait for it to finish). So whatever it is, it's not memory.There currently exists a Windows XP installation but that shouldn't have any affect. Windows XP loads up just fine - no hardware/boot problems whatsoever. Something is confusing Ubuntu. Any ideas? I'd rather like to do the Open Source route and remove Windows from my home computers if I can.

Any suggestions/opinions/reference links?

Help much appreciated!

Arron

---

### Post by FuturePilot on 2007-04-10
It sounds like this might be something with the computer and not the CDs. I've had a similar problem and for me the solution was to flash the BIOS. I know that sounds crazy, it definitely was not the first thing I thought of. But it's worth a shot. 

Also if you have more than one CD drive, maybe try the other one. You might want to try this first before messing with the BIOS if you have 2 CD drives. For me the Ubuntu CD only boots correctly from one of my CD drives.

---

### Post by Geekkit on 2007-04-10
> **FuturePilot said:**
> It sounds like this might be something with the computer and not the CDs. I've had a similar problem and for me the solution was to flash the BIOS. I know that sounds crazy, it definitely was not the first thing I thought of. But it's worth a shot. 

Also if you have more than one CD drive, maybe try the other one. You might want to try this first before messing with the BIOS if you have 2 CD drives. For me the Ubuntu CD only boots correctly from one of my CD drives.

Thanks, I found a link:

[http://ubuntu1501.blogspot.com/2007/01/installing-ubuntu-on-your-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/installing-ubuntu-on-your-dell-1501.html)

which suggests it might have something to do with Ubuntu not recognizing the SATA drives. It suggests diddling with the command prompt after pressing F6. I'm going to try this now ... wish me luck.  :)

---

### Post by Geekkit on 2007-04-11
> **FuturePilot said:**
> It sounds like this might be something with the computer and not the CDs. I've had a similar problem and for me the solution was to flash the BIOS. I know that sounds crazy, it definitely was not the first thing I thought of. But it's worth a shot. 

Also if you have more than one CD drive, maybe try the other one. You might want to try this first before messing with the BIOS if you have 2 CD drives. For me the Ubuntu CD only boots correctly from one of my CD drives.

FuturePilot:

It appears that you're suggestion to give the BIOS the Vulcan nerve pinch did the trick. Setting the BIOS to its defaults appears to have worked. I am currently doing this off the live CD.

If any mods/ops are watching this posting it might make sense to sticky this post or possibly put up a quick note telling users to reset their BIOS if they have run out of options. I've seen quite a few posts in this forum and others for that matter where users have had freezes after the initial attempt to install. This seems to be the magic key.

Thanks again FuturePilot.

:)

---

### Post by FuturePilot on 2007-04-11
No problem.:)  I had that problem where the install just froze right in the middle even after several attempts. Flashed the BIOS and it worked.

---

### Post by Overseer10 on 2007-04-11
I've almost the same computer, did the same thing to the booting order. But I still get freezed over the same issue " PCI: cannot locate resource region 3 of device 0000.000.00.0" it always freezes even on the alternate version of the installer :(

---

