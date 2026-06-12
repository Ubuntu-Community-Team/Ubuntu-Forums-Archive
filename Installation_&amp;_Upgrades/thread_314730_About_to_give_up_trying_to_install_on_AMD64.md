---
title: "About to give up trying to install on AMD64"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by omegahelix on 2006-12-08
Hello.

I've been trying to install Edgy for several nights now and I am about to give up out of frustration.  I have the following hardware:

AMD64 FX-55 Processor
Soltek K8T-Pro 939 Motherboard
Gigabyte ATI X800XT Platinum 256MB AGP Graphics Card
1GB Corsair Ram
Samsung SyncMaster 710T 17" LCD
Lite On 1633S Dual Layer DVD Burner
Microsoft USB Laser Mouse
Logitech Elite USB Keyboard

I have tried the 64 Bit Live CD, 64 Bit Alternate CD and 32 Bit Alternate CD.  I am able to boot up from CD and I get the installation menu but crash right after.  I have tried the OEM installation and the custom installation with various combinations of one or more of the following options: mem=512m, fb=false, irqpoll, pci=noacpi, noapic, nolapic, acpi=off, acpi=force.  I have tried turning off active power mgmt, AMD Cool & Quiet and ACPI in the BIOS.  Nothing is working.  I see the kernel uncompress and start to boot via the text output and then it hangs after loading the keyboard and mouse USB "HID" stuff.  I tried disabling "legacy USB support" in the BIOS but that just made my mouse/KB not work.  At other times I have gotten the "Kernel Panic Not Synching" message with something about ACPI or APIC above it.

I have had Dapper working on my system in the past so I downloaded the Dapper Alternate 64 Bit CD and that loads up the GUI installer and I am able to enter my time zone, etc. but then it starts complaining about packages being corrupt.

Does anyone have any idea what might be going on?  This is a nightmare.  Thanks.

---

### Post by unisol on 2006-12-08
check cd for errors. burn at a low speed 4x or less, check memory

---

### Post by omegahelix on 2006-12-09
IT WORKS!!!  :p 

I think what it came down to is I was not waiting long enough for the installer to continue after it loaded my USB devices.  It took like 5 minutes and then another 5 for "Attempting to start the frame buffer..." but then the rest went fast.  I installed in Edgy AMD64 in OEM mode from the Alternate CD with no boot arguments.  I even got my wireless card (Linksys WMP54G) working!  I'm posting this from Edgy right now!

---

