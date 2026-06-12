---
title: "Intrepid installation problem: Loading hardware drivers"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eusonlito on 2008-10-21
I can't install Ubuntu Intrepid because the installer always stops in the "Loading hardware drivers" line.

No errors or messages, only stop. After this message don't work the keyboard.

My hardware:

Motherboard: Gigabyte GA-EP35C-DS3R
Processor: INTEL CORE2QUAD Q9550 (No Overclocking)
Hard Disks: WD RE3 WD5002ABYS - Maxtor 6V320F0 - Maxtor 6Y160M0
SATA RAID/HCI Mode: IDE
RAM: 4Gb Kingston DDR3 1333
Graphics: ASUS EAH3650 PCI-E
PCI: D-Link AirPlus DWL-G520
IDE: DVD RW - Combo CDR + DVD

I had tried a lot of different configs but no works any.

Thanks for your help :)

---

### Post by Pumalite on 2008-10-21
Try Intrapid Alternate CD 64 bit

---

### Post by eusonlito on 2008-10-21
Ok, I'm downloading.

I had tested with 64 and 32 bits versions but not the alternate.

Thanks and I will comment the result.

---

### Post by eusonlito on 2008-10-21
It works!!!

Thanks a lot

I will enjoy now with my new Ubuntu ;)

---

### Post by Pumalite on 2008-10-21
Glad it worked. Good luck!

---

### Post by eusonlito on 2008-10-21
Sorry, after installation ubuntu it's locked again like in the live CD.

It's a ******* problem...

I will try other solutions (Which?)

Bye and thanks.

---

### Post by Pumalite on 2008-10-21
Do you see Grub? What's your exact error message?

---

### Post by eusonlito on 2008-10-21
I have found the problem, without the D-Link AirPlus DWL-G520 PCI card the Live CD and installation works fine.

I think that it's a driver problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263059](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263059)

Thanks a lot for your help :)

I will reinstall again the system without the PCI card and I will add it when the kernel/driver works fine.

---

### Post by MacUntu on 2008-10-21
I'm sorry to tell you, but your problem is not related to this bug (which in addition is already fixed).

Maybe you should open a new bug report for your problem.

---

