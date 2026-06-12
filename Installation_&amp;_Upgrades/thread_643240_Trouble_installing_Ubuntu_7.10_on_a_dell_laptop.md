---
title: "Trouble installing Ubuntu 7.10 on a dell laptop"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by tj2131 on 2007-12-17
Im having a heck of a time getting Ubuntu 7.10 install on my Dell Inspiron 5150. I boot to the live disc, then click on the install icon and everything goes fine from there but when i reboot the system after the install. the GRUB bootloader comes up and I select Ubuntu and its starts to load. Shortly after it begins to load its get stuck on teh default orange background and I get nothing else, no mouse or anything. I have tried installing from 4 different discs burned from different images, I have check the discs over before installing from them.

I am running out of ideas on what could be causing it. Any tips or help would be great.

Thanks,
TJ


Dell Inspiron 5150
P4 3.0GHz
1.5G RAM
120 GB WD drive
ATI Radeon 9000

---

### Post by Pumalite on 2007-12-17
Use the Alternate CD.

---

### Post by tj2131 on 2007-12-17
Thanks, I am somewhat new to this I have been using Ubuntu on my desktop for 6 months now and have not had any problems, so I decided to put it on my laptop.
I'll give it a try now :)

TJ

---

### Post by Pumalite on 2007-12-17
[http://ubuntuforums.org/showthread.php?t=636401](http://ubuntuforums.org/showthread.php?t=636401)
[http://www.linux-on-laptops.com/dell.html](http://www.linux-on-laptops.com/dell.html)

---

### Post by tj2131 on 2007-12-17
I downloaded and installed the Alternate version that you recommended and its does teh same thing.

Thanks,
TJ

---

### Post by Pumalite on 2007-12-17
Read the links I gave you. You might discover something that helps you. If you want to try some boot parameters with your Live CD; here is a guide and a collection of them:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by tj2131 on 2007-12-17
Yea I just tried editing the boot parameters and I still got the same thing.

TJ

---

### Post by Pumalite on 2007-12-17
Try other distros to see if you are incompatible with Linux in general or Ubuntu in particular.

---

### Post by tj2131 on 2007-12-17
Well I did some more research and I downloaded Ubuntu 7.04 and that install fine and work great. But when I upgrade that to 7.10 I run into the same issue, so I guess I will just stay with 7.04 for now until a new kernel is released. Previous to this I had Fedora installed and that worked great also, Although i am still open to ideas.

Thanks Pumalite for all your help!

TJ:)

---

### Post by Pumalite on 2007-12-18
Quite welcome. Good luck.

---

### Post by John Matrix on 2007-12-29
Seems to be the problem discussed here:

[http://ubuntuforums.org/showthread.php?t=651916](http://ubuntuforums.org/showthread.php?t=651916)

[https://bugs.launchpad.net/ubuntu/+bug/146707](https://bugs.launchpad.net/ubuntu/+bug/146707)

---

