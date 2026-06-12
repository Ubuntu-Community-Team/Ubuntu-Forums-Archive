---
title: "Ubuntu and Xubuntu won't install on this laptop, complains about bios"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by benanderson on 2007-05-11
I have an old IPC Topnote F laptop, Model 200... It's at least 5 to 6 years old now! Anyway, I tried to install Ubuntu, no dice... it just got stuck on a blank screen with a flashing cursor, so I tried XUbuntu instead. The furthest I get is a blue screen with a mouse pointer. I can't move the pointer and no key combinations work. When I booted XUbuntu from the text boot menu (after pressing the escape key from the graphical boot menu) I get a brief message saying something about how my BIOS is from 1999 and that a BIOS from 2000 is needed, I can't flash the BIOS because the people who made it have gone out of business and the lowest model supported on the IPC site is the model 210. I don't know whats wrong and I want to get XP off of this thing because it runs way to slow because it has too load all that anti-virus and anti spywear crap at boot

Here are the laptop's specs;
CPU: Intel Celeron 997MHz, L1 = 16kb, L2 = 256kb
Motherboard Manufacturer/Chipset: Motavita/SiS 630
BIOS: Insydew Version 0.03
BIOS date: 15th - Nov - '99
Memory: PC133 SDRAM, 128MB (96MB Available to operating system, 32MB for shared graphics memory)
Network: Realteck RTL8139 Family PCI Fast Ethernet Modem, Unknown PCI dialup modem
Media: Internal IDE 10GB HDD, Internal CDROM 24x, Internal Floppy disk, 2x USB1.1 ports
Sound: SiS 7018 Wave
Graphics: SiS/300/305/630/540/730 32MB shared graphics @ 1024x768, 13.1" TFT

Thanks in advance for the help =]

Ben

---

### Post by Matty2006 on 2007-05-11
First thing I would do.. is go hunt for a new bios image if possible to upgrade to latest.
If this rig is pretty old you may be SOL as far as updating goes.. Also some bios settings have a place to set the  hardware detection for the OS. I dont know the exact line item.. but taking a look though the settings wouldnt hurt.

Next on these older rigs, you may be better off with the alternate install CD instead of the Live CD.. 
When starting up the install Boot see if you can turn off acpi and or pcmcia.. There should be a number of switches that can be tried.

Good luck

---

### Post by benanderson on 2007-05-12
> **Matty2006 said:**
> First thing I would do.. is go hunt for a new bios image if possible to upgrade to latest.
If this rig is pretty old you may be SOL as far as updating goes.. Also some bios settings have a place to set the  hardware detection for the OS. I dont know the exact line item.. but taking a look though the settings wouldnt hurt.

Next on these older rigs, you may be better off with the alternate install CD instead of the Live CD.. 
When starting up the install Boot see if you can turn off acpi and or pcmcia.. There should be a number of switches that can be tried.

Good luck

The BIOS is so out of date I have non of those settings, just shared memory, boot priority and password.
Good thing is that I found a BIOS image, not bleeding edge but it was from late 2000.
The bad thing is after flashing the BIOS I ran into a bit of a problem. I started my laptop and I was greeted with nothing! BIOS doesn't even start! No post beep, no flashing LEDs, NOTHING! Have any idea on that? Or do I need to send this thing to silicon heaven? Or an even better idea, know anywhere in the UK that sells laptop motherboards? The case looks good and it's like a rock! Nice 'n sturdy =]

---

