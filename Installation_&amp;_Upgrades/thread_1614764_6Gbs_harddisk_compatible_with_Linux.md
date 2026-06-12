---
title: "6Gb/s harddisk compatible with Linux?"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by Dr.LY on 2010-11-06
I have 2 6Gb/s harddisks and under Win7 they work fine.  When I try to boot from a live USB to install Ubuntu it does not see a harddisk.  I've been trying for 2 weeks now to install; tried modifying GRUB boot options, fdisk, searched forums, followed a lot of tips, but nothing helped...

Until yesterday I found 1 thread that says Linux is not compatible with 6Gb/s harddisks?

Anyone heard of this?

---

### Post by dino99 on 2010-11-06
never heard about that, might be a fake (again)

use partedmagic to prepare your hdd

---

### Post by sikander3786 on 2010-11-06
> 
Until yesterday I found 1 thread that says Linux is not compatible with 6Gb/s harddisks?

I think I have heard that somewhere too.

If you've got a standard Sata controller on your motherboard apart from that 6Gb/s controller, try connecting your HDD to that and see if it is detected now.

---

### Post by arnavk007 on 2010-11-06
linux will not support the extra 6 Gb/s controller
which chipset do you use
AMD 890GX/FX would work fine as in those chipset 6 GB/s support is native

---

### Post by P4man on 2010-11-06
sure linux supports sata 3 (=6Gb/s). Check your bios and see if you havent configured your drives for RAID or for IDE compatibility instead of native sata (achi). Beware that changing this setting will cause windows to bluescreen until you change it back.

If that doesnt help provide the output of

```
lspci  
```

and 

```
sudo fdisk -l
```

---

### Post by Dr.LY on 2010-11-06
> **arnavk007 said:**
> linux will not support the extra 6 Gb/s controller
which chipset do you use
AMD 890GX/FX would work fine as in those chipset 6 GB/s support is native
motherboard = gigabyte GA-X58A-UD7

_chipset_
North Bridge: Intel® X58 Express Chipset 
South Bridge: Intel® ICH10R - storage interface (for the 6Gb/s SATA) = Marvell 9128 chip

---

### Post by P4man on 2010-11-06
Marvel 9128 is definately supported by the kernel. You likely have it set to RAID mode in the bios. Or the drives contain raid metadata. Check disk utility from system > administrion > disk utility.

To tell you the truth however, you will get better performance connecting the drives to the sata ports of your southbridge. That goes for both windows and linux. Those marvell chips are crappy and the only reason they are put on motherboards is to have fakeraids (bios raids), which again is only something that makes sense for windows, since windows cant boot from a pure software raid. If you dont need the fakeraid to boot windows from a raid, dont use those ports.

Unless you have uber fast SSDs, the faster interface speed is rather pointless as no harddive comes close to those speeds anyhow. I guess "6gb/s" looks good on the cardboard box though.

---

### Post by Dr.LY on 2010-11-06
> **P4man said:**
> 
Unless you have uber fast SSDs, the faster interface speed is rather pointless as no harddive comes close to those speeds anyhow. I guess "6gb/s" looks good on the cardboard box though.

I have 2 WD Caviar Black 640GB installed that were sold to me as being 6Gb/s.  Or am I understanding this not correct?

I'll check out the RAID settings in the BIOS, but as far as I know I never configured any RAID in the BIOS

thanks for a quick reply

---

### Post by P4man on 2010-11-06
> **Dr.LY said:**
> I have 2 WD Caviar Black 640GB installed that were sold to me as being 6Gb/s.  Or am I understanding this not correct?

Thats the speed of the interface between the drive and the controller. The harddrive itself would at the very best be able to sustain 200 Mbyte/s sec, which is ~1.6 GBit. Its probably closer to half of that though, so the 6 gbit interface is total overkill for a normal harddrive (only the fastest SSDs could see a benefit).

Theoretically there would be a small benefit when data is read from the drive's cache (which is faster) but that advantage is quicly lost to the fact the controller is connected to the southbridge rather than closely integrated.

Long story short: the other sata headers will almost certainly perform better.

> 
I'll check out the RAID settings in the BIOS, but as far as I know I never configured any RAID in the BIOS

Could well be the default setting.

---

### Post by Dr.LY on 2010-11-07
> **P4man said:**
> sure linux supports sata 3 (=6Gb/s). Check your bios and see if you havent configured your drives for RAID or for IDE compatibility instead of native sata (achi). Beware that changing this setting will cause windows to bluescreen until you change it back.



In Disk Utility I can see two different host adapters: 4x PATA (driver pata_jmicron) en 2x SATA (driver ahci).  If I changed in BIOS the SATA to AHCI instead of IDE, the drives were indeed recognized. But also blue screen in Win7.
So I installed another drive on a PATA adapter and was able to install Ubuntu on it.  F12 during boot lets me choose which harddisk I want to boot now.  Ubuntu can only see the drive on the PATA adapter; win7 can see all the drives.  Maybe not perfect but it works for now

Thanks for the help

---

### Post by P4man on 2010-11-07
> **Dr.LY said:**
> In Disk Utility I can see two different host adapters: 4x PATA (driver pata_jmicron) en 2x SATA (driver ahci).  If I changed in BIOS the SATA to AHCI instead of IDE, the drives were indeed recognized. But also blue screen in Win7.

I told you :).

If you ever intend to reinstall windows, set those drives back to achi. NOt only do they then work with linux, they will also perform better.  It might be possible to make it work without reinstalling, but I have no idea.

---

