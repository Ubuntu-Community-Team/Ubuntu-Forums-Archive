---
title: "SATA Drive Not Detected"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by shrtysk8r1 on 2007-07-22
I recently upgraded my hardware to the following:

Intel Core 2 Duo E6600
2 GB RAM
8800 GTS 640MB
Abit IP35-E Mobo (P35 Chipset)
74GB SATA WD Raptor

The live cd boots and operates without issue, however, when I go to install my SATA HD is not detected. I have installed Ubuntu multiple times with older hardware (and the same HD) so I believe this is a chipset/mobo issue. Does anyone know of a solution?

---

### Post by Pumalite on 2007-07-22
Try going to your BIOS>IDE Configuration>Advanced Support, and make sure is set to: 'Advanced Support for PATA+SATA'

---

### Post by shrtysk8r1 on 2007-07-24
Thanks for the response, however - I have no such option in my BIOS.

---

### Post by Pumalite on 2007-07-24
Try Text Mode> Ubuntu Alternate CD. Avoid possible hardware problems. Especially your 8800 Nvidia card or other hardware problems. Check for loose connections etc.

---

### Post by shrtysk8r1 on 2007-07-28
It seems I was only able to install ubuntu when my drive was NOT partitioned before (full working windows xp install). If i created a partition with Gparted Live CD, then it wouldn't show up in the installation dialog. I was able to install ubuntu with the "Guided - resize primary partition and use remaining free space" option, but I can't get it to boot.

---

### Post by Pumalite on 2007-07-28
Use Super Grub to detect your system and re-install Grub if necessary: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
You can use these guidelines if you prefer ( and have a Live CD ):

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by shrtysk8r1 on 2007-07-29
Well, GRUB works fine - I can still boot into my windows installation, and one random time I was able to get into ubuntu and apply updates.

---

### Post by pcmanlin on 2007-07-29
Feisty or edgy?

P35 used ICH9, 2.6.18 can not run on some P35 motherboard.

But i haved compiled a new 2.6.20 kernel, it works.

---

### Post by shrtysk8r1 on 2007-07-29
Feisty, and I'm on it now. It only seems to boot to ubuntu after long periods of having the computer off. Windows works fine.

---

### Post by fredj on 2007-07-31
Go into your bios and go to Integrated Peripherals->Onchip Sata Device. Look at the OnChip
Sata Mode.
It is probably set to IDE by default and windows is happy to work with that mode. However
the latest Linux kernels prefer it to be set to the more advanced AHCI mode.
The trouble is that if you change it now, you will find Ubuntu boot works better but probably
Windows won't boot until you change it back again.

---

### Post by onlyconnect on 2007-07-31
> the latest Linux kernels prefer it to be set to the more advanced AHCI mode.
Thanks, that appears to have fixed my RAID problem too.

Tim

---

### Post by fredj on 2007-08-01
The answer to all these problems for the IP35 and for the IP35-E seems to be to set your SATA
drive (in the bios) to AHCI mode. Then use the Abit CD to make a floppy disk with the SATA
drivers. Install Windows XP using the floppy disk when requested. Then install Ubuntu using the
Alternate install CD. That is what worked for me.

---

### Post by shrtysk8r1 on 2007-08-13
I have no such option in my IP35-E BIOS. Is this feature made available through an update or is it specific to the IP35?

---

### Post by fredj on 2007-08-13
Looking in the motherboard manual I see that you can set the SATA mode only on the IP35
and not on the IP35 - E. I suggest you get in touch with ABIT support.

---

### Post by Waves77 on 2007-08-16
> **fredj said:**
> The answer to all these problems for the IP35 and for the IP35-E seems to be to set your SATA
drive (in the bios) to AHCI mode. Then use the Abit CD to make a floppy disk with the SATA
drivers. Install Windows XP using the floppy disk when requested. Then install Ubuntu using the
Alternate install CD. That is what worked for me.

I came across this thread and I'm having the same problem... WD Caviar 750G Sata drive... would you mind telling me what driver you used? The installer isn't finding anything...

---

### Post by dkaplowitz on 2007-12-09
> **fredj said:**
> Go into your bios and go to Integrated Peripherals->Onchip Sata Device. Look at the OnChip
Sata Mode.
It is probably set to IDE by default and windows is happy to work with that mode. However
the latest Linux kernels prefer it to be set to the more advanced AHCI mode.
The trouble is that if you change it now, you will find Ubuntu boot works better but probably
Windows won't boot until you change it back again.
That has been my experience so far (running an IP35 Pro). Has anyone found a way to work around this without having to change the BIOS setting? I'd hate to have to reinstall Vista, but I guess if I had to I could.

---

### Post by joshlos on 2007-12-13
ACHI wouldn't work for me, but RAID did. Windows, as someone said before, only worked with IDE (I tried all 3 settings before installing XP and Kubuntu).

Is there any way to make Kubuntu cooperate with IDE now that both OSs are happily installed? I would prefer to not have to go into BIOS before each boot to flip flop the settings.

Has anyone tried to update the BIOS? Is there some sort of edit I can do to GRUB/Kubuntu to make it IDE happy?

---

