---
title: "Install Problem: Acer Veriton 5100"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by netpres on 2006-11-23
Hi

I've got an old box (Acer Veriton 5100 P3/800 512Mb/20Gb) that refuses to start the live CD.

I've used the disc on two other machines without any drama, but this box is causing grief.

I've checked the forums, disabled ACPI, X starts, but I don't get any further display. I've left it for 30mins with no disc activity (in case it was still working in the background), but still no luck.

Any thoughts?

Greg

---

### Post by xenoalien on 2006-11-23
Try a different cd-rom cause I know my old pcs cant read a burnt cd.

---

### Post by netpres on 2006-11-23
Using a newish DVD-RW and can read any other disc.

---

### Post by netpres on 2006-11-25
Looks like it's Gnome that's causing problems. System boots fine with Kubuntu. Will have to do more experimentation.

---

### Post by ebaymic on 2007-07-05
I have recently obtained an Acer Veriton 5100 and came across the same mentioned problems with the live CD getting stuck in the Gnome Desktop boot screen.

I have managed to find a work around to get the CD to load correctly. Seems to be an issue with ACPI with this PC. Have read that some Bois's are not totally compatible to Linux need the ACPI feature disabled.

To boot the Ubuntu or Linux Mint CD ( in my case) in the boot Menu I pushed the F6 Accessibility Key and then entered acpi=off . This disables acpi in the kernel.

Once the operating system is installed Grub loader has to be changed. In /boot/grub/menu.1st add or modify acpi=off (may have to change it from "on")

title Linux Mint, kernel 2.6.20-16-386
root (hd0,5)
kernel /boot/vmlinuz-2.6.20-16-386 root=UUID=aff2d45f-d9c6-4352-89cf-f6cf42ad7c5e ro quiet splash acpi=off
initrd /boot/initrd.img-2.6.20-16-386
quiet

After that everything so far works. Previously I could not get the sound card, Network Card and USB ports to work. Everything seem to be recognised but did not do anything.

Hope that Helps.

---

