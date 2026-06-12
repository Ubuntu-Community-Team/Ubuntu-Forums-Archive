---
title: "New build - do I need to install intel chipset?"
date: 2014-02-13
forum: Installation &amp; Upgrades
---

### Post by samwillc on 2014-02-13
Hi,

This may seem daft but I'm looking at my brand new z87 gryphon motherboard and the accompanying dvd and wondering how I'm going to install whatever's on that dvd.

I plan to install elementaryOS based on ubuntu 12.04 right from the start once this thing is built. I plan to run windows in virtualbox as and when I need to.

I've installed eOS on my other desktop so I was hoping just to be able to do the same once this is built. However, what do I do about the drivers and chipset and stuff on this dvd? Are they intended just for windows? In which case I could install the appropriate things when running windows in virtualbox. Some help would be most appreciated.

Thanks.

Sam.

---

### Post by Bucky Ball on 2014-02-13
It will say on the disk, but yes, probably for Windows. Therefore, irrelevant in Linux. If you decide to use Windows, you are going to need them I imagine, but not for Linux.

---

### Post by samwillc on 2014-02-13
> **Bucky Ball said:**
> It will say on the disk, but yes, probably for Windows. Therefore, irrelevant in Linux. If you decide to use Windows, you are going to need them I imagine, but not for Linux.

Hi, thanks. It's a windows dvd (for asus z87 gryphon motherboard) with drivers but also software for various things that I'll never use. I will just install this stuff in virtualbox then. I'm guessing I need this disk in order for internet/wireless/bluetooth, that sort of thing to work, in windows.

---

### Post by Frogs Hair on 2014-02-13
When I built my desktop there was software necessary for installation prior to installing the operating system. While some was needed other packages were specially for programs that only run in Windows once it was installed.

---

### Post by Bucky Ball on 2014-02-13
> **samwillc said:**
>  I'm guessing I need this disk in order for internet/wireless/bluetooth, that sort of thing to work, in windows.

Yes, in Windows. All taken care of in Ubuntu. Those things will, hopefully, 'just work'. Many drivers are built right into the kernel. Network Manager deals with wireless/internet (and there are other options) and Bluez (normally) looks after bluetooth. Both should 'just work'. Post a new thread about it if they don't. ;)

---

### Post by mastablasta on 2014-02-14
also i don't think they will work in virtualbox since virtual mashcine uses it's own drivers

---

### Post by oldfred on 2014-02-14
You also have to decide whether you want the newer UEFI with gpt partitioning or the old BIOS with MBR partitioning.
Not sure if virtual box is updated for UEFI and gpt.

Also even Ubuntu is just catching up with the latest Intel updates to kernel, support software, and video drivers, so if your distribution is not based on the very newest it may not work well.
May also depend on what video you have, Intel from chip or add-in video card.

       Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)
Intel "Haswell" System 76 Iris Pro Linux Graphics Yield Some Wins Against Windows
[http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1)

 NVIDIA's Linux Driver On Ubuntu Is Very Competitive With Windows 8
[http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1)

---

