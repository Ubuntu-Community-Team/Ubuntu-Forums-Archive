---
title: "Live CD Problems.."
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by loincloth170 on 2006-12-05
Hello, I'm just getting started with Ubuntu (and with Linux in general), but I'm having some problems getting Edgy to work properly. The first time I loaded the live CD up, it gave me a "Kernel panic - not syncing: IO-APIC + timer doesn't work try using 'noapic'. Looking around on the internet I got it to continue past that using "live noapic nolapic". I thought I had it figured out only to find that it now gave me a "VFS: Unable to mount root fs on unknown block" error. I can't figure it out!

I have a AMD Athlon 64 X2 4200+ (Windsor), Asus M2N32 SLI Delux, 1GB of Corsair DDR2 800, 80 GB WD800JD harddrive, and my monitor is a HP vs15.

---

### Post by louieb on 2006-12-05
Booting from a live Linux CD is hit or miss. Try this option or that. I saw one post where the guy had to take out all but 1 stick of  memory before the  CD would boot.  The first boot option I try  is  ide=nodma but most of my PC's are a lot older and slower that yours. 
Get the Knoppix Live CD and  see if that boots up. I don't know of a distribution that is better at hardware detection.

---

### Post by dinub1 on 2006-12-05
What type of graphic card you have ? Is it an ATI RAdeon PCI-E of the newer types ? If so that is your problem. I have problems with mine too.

Ubuntu apparently knows to work better with older ATI cards but the newer ones are problematic. ATI in general is problematic with Linux distros in general.

---

### Post by wpshooter on 2006-12-05
Are you checking the integrity of your Ubuntu CD by running the verification test found on the initial Ubuntu boot screen menu ?

---

### Post by loincloth170 on 2006-12-05
Actually with some messing around I managed to get it to work after two different tries by adding noapic nolapic to the end of the boot line. I then installed it, but had to switch back to Windows for the time being so I am not sure if it is fully functional. Thanks for everyone's help!

---

