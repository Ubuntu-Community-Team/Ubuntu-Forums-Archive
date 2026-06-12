---
title: "AMD64 Install"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by cfaulkner on 2007-04-26
**System Specs:**

Gigabyte GA-M57SLI-S4 Motherboard  (570-SLI Chipset)
Athlon X2 3800+ Dual Core Processor
Corsair 5-5-5-18 512mb x2  (1gb total) DD2 800 Ram
eVGA Nvidia 7600GT Graphics card
320 gb SATA 3Gb/s drive
20.1 Starlogic FP Monitor (1680x1050 Max res)
19 Starlogic FP Monitor (1280x1024 Max Res)

Nothing else but a DVD 16 x burner and crappy keyboard and a nice Logitech mouse

**Problem:**

Boot Normally, Kernel hangs before it gets properly loaded, forgot the error code.

Boot with "noapic", System loads off the cd just fine but the screen res is at 640x480 and can't be changed.  Can't install because I can't see the buttons down below and I don't want to mess anything up just by hitting enter cause I don't know what i'm hitting enter for.. :)

Boot with "ACPI=off", same as noapic

Boot with "ACPI=off noapic pci=noapic nolapic" same problem as just noapic

-----
Basically, this just happens with ANY distro of linux.  I can never use X to install any distro, Gentoo, OpenSUSE, Fedora, you name it...  Doesn't work...

I really don't know what i'm doing wrong or if i'm over looking something, but if someone can shed some light on this matter, i'd appreciate it.  I could install Ubuntu from console I guess, cause I was always able to install Gentoo or OpenSUSE from console fairly easily.  I'm just wondering if there is a work-around, something i'm missing or what.  Just wondering why can't Ubuntu 7.04 amd64 livecd work right out the box. :)

Thanks in advance!

---

### Post by cfaulkner on 2007-04-26
Any thoughts? I've posted my Rig.  Don't make me go back to Gentoo... lol

---

### Post by SuperDuperCruizer on 2007-04-29
I'm working with similar hardware:

 GA-M57SLI-S4 ver 1.0
1Gb Patriot Mem (512 x 2)
Logitech DeNovo Edge (the touchpad works great with latest ver. of Ubuntu)

I'm trying to install xp64 Pro and Ubunto Fiesty 64 in dual boot configuration.   I've been able to get Ubuntu installed (hit F6, remove 'quiet splash' insert 'noapic'), but after running live/install there's a hangup with Grub during restart.  I'm looking into editing Grub (I'm a newbe to Linux).  Also,  xp64 Pro hangs up on startup after dual boot install.  How far have you gotten?

SuperDuperCruizer

---

