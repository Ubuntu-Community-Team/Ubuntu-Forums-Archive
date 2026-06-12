---
title: "Grub hangs with extra sata drive via pci"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by kwadronaut on 2005-05-08
I installed a pci sata-controller wich seems to work. But when I switch the computer off, attach the satadrive and restart Grub fails to load any OS, nor Ubuntu nor Win2k pro. It just gives me a black screen after choosing the os.

I've tried to find solutions or workarounds but it seems that no-one had the same problem.

My config: 
A7v8x-x motherboard with amd 2500xp
hda = maxtor 120 ide
hdb = maxtor 80gb ide
diskdrive
removable optical storage..

->pci mentor Serial ATA Multi-Channel PCI Host Controller with Silicon Image 3112 chipset/drivers
->maxtor maxline II plus 250 gb

The first time i installed the drivers under win2k I thought it went well, but while trying to format it into fat32 it gave an error. So i tried to reboot and figured out that I have a problem...

Every suggestion is appreciated after spending 2 days of searching, looking, trying and failing.

Edit: I thought of extra information, I got the error messages when trying to make a partition of about 90gb and then formatting it. Maybe that partition was too big. But i can't load anything (not even a livecd) when the extra disk is attached so i can't wipe everything out.

---

### Post by pazuzuzu on 2008-04-23
It would appear to me that adding the new SATA disk and PCI-SATA adapter has probably confused either GRUB or udev (Ubuntu doesn't still used devfs, does it?) and most likely GRUB is attempting to load a / partition which doesn't exist or isn't formatted correctly or boot a kernel which doesn't exist.  I'd suggest you re-run the install disk and see what happens.

This advice is based on my experience with using a PCI-IDE adapter on Gentoo; I'm guessing it will probably carry over to Ubuntu-land.

---

