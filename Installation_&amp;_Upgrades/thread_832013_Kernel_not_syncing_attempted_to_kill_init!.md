---
title: "Kernel not syncing: attempted to kill init!"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by jcarroca on 2008-06-17
Hi,
I installed 8.04 via a downloaded iso on an extra 100g SATA hard drive.  The system has also 2 other hard drives that are setup to run Windows XP.  Ubuntu installed fine the 1st time but was unstable so I tried to reinstall using the bootable disk.  Thats when I got the "Kernel not syncing:attempted to kill init" error.  I have tried to load with safe graphics, and many boot parameters such as noapic nolapic, acpi=off, irqpoll, lapic pci=routeirq nothing seems to work.  I am able to boot to the ubuntu screen but can not go much farther.  This is my second CD that was downloaded and burned so I don't think it is the CD.  I have sent for an official CD from Ubuntu to check that.  Any ideas on what might be the problem.  Windows XP works fine on all hard drives so I know its not a hardware issue.

---

### Post by Pumalite on 2008-06-17
Burn a new CD. Do md5sum, burn at 4x or less.

---

### Post by jcarroca on 2008-06-17
I used digestIt to verify the hash.  the hash number from the forum [http://ubuntuforums.org/archive/index.php/t-765178.html](http://ubuntuforums.org/archive/index.php/t-765178.html), 8895167a794c5d8dedcc312fc62f1f1f matches my downloaded iso perfectly.

---

### Post by Pumalite on 2008-06-17
Did you burn at 4x or less?. Did you check CD integrity before install?
Clean the lens in your burner, just in case.

---

### Post by jcarroca on 2008-06-19
The disc was burned at 4X so that was not the issue.  However, I did find out the problem.  It was somewhere in my bios.  Don't know where, but I put my setting to the default (not optimized) setting and now it installed fine.  Thanks for all your help.  I am sick of the many crashes associated with Windows and am eager to find a more stable environment.  I just need to convince the wife and kids of this. :)

---

