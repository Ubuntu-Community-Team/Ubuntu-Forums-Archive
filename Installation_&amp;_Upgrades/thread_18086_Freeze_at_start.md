---
title: "Freeze at start"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by skd on 2005-03-04
Well, i tried to try ubuntu live cd. It booted, i selected to boot Ubuntu, then some text ran quickly, the screen turned black and freezed. Then i tried to install cd. It booted, then i pressed enter and then black screen with a blinking cursor. I've waited 10 mins and made conclusion, that it freezed.

Any help?

PIII - 0,5 GHz; 256 Mb RAM; nVidia TNT 16 Mb; Original warty ubuntu cds v4.10

---

### Post by alastair on 2005-03-04
Try the latest Hoary install CD :

[http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/hoary/array-6/](http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/hoary/array-6/)

---

### Post by skd on 2005-03-06
it would take too long for downloading it... i gues i have to wait when it would be able for shipping :)

---

### Post by alastair on 2005-03-06
OK - then try ...

When you get the prompt and you normally hit <ENTER> to install/run, type :

linux acpi=off noapic

---

### Post by dmallery on 2005-03-09
hi

i have the same problem on aa supermicor 370de6 mobo. "starting hotplug subsystem.".. freeze.

have spent a full day or more trying every permutation of noapic, acpi=off, noacpi, pci=noacpi, etc.

funny the above work for some and not here.   there is an apic problem with this mobo.  you get an error message: "MP BIOS 8254 not connected to IO-APIC" .  putting "noapic" into the boot line makes it go away.

i can't download the new install cuz my satellite connection only gives me about 28kB/sec for some reason.  i will be in a motel tonite and try it there!

i searched all the mailing lists, finding nothing beyond what i tried above.

thanks for any suggestions.

dave mallery

---

### Post by blackpanther989 on 2005-03-09
this may sound silly but i had a similar problem. 


i had 2 video cards in the machine and it only configured one. my monitor was plugged into the other one. so while it worked during the install X did not recognize the 2nd card.

---

### Post by neuneu on 2005-03-09
Hi,

 [-( I am having the same problem
My Computer is a server:

Proliant ML370, 2 HD 36 GB with RAID 1+0 (hardware)
I algo get the black screen after installation
 Thanks for any help

---

