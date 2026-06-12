---
title: "Installer Doesn't see Hard Drive"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by medw1974 on 2005-11-22
Hi

My PC has an Asus p5ld2 m/board and has 2 hard drives - 1 80gb sata and a 40gb pata ide drive which uses the ITE8211F IDE controller rather than the boards standard udma controller. It is this IDE drive that I want to install ubuntu on but it is not seen at the partition stage. I'm guessing this is because the installer doesnt load a driver for the controller so is there a module line or something I could add.

What is really frustrating is that Mandriva and SuSE recognize the drive with no problems at all.

Any help would be greatly appreciated.

Thanks

Michael

---

### Post by medw1974 on 2005-11-23
I've figured that my problem is there is no built in driver support for the IT8211 ide controller so I've found a linux driver for it.

Next problem is how to actually load it as I don't have a floppy drive on the system. Could I use a USB drive? Any pointers anyone?

Michael

---

### Post by nighthawk39 on 2005-11-26
[QUOTE=medw1974]I've figured that my problem is there is no built in driver support for the IT8211 ide controller so I've found a linux driver for it.

Next problem is how to actually load it as I don't have a floppy drive on the system. Could I use a USB drive? Any pointers anyone?

Michael[/QUOTE]
Can you give me a link to the Linux driver? I have the exact same problem with my IT8211 controller.   (although I do have a floppy drive)

---

