---
title: "Installing Ubuntu on a Acer 5050"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by dancingbear909 on 2008-08-04
I have an ACER 5050 with theses specs, currently running Fedora 9, but, I would like to run Ubuntu on this notebook.

•  Processor: AMD Turion64 x2 TL-50 (1.6 GHz, 512 KB L2 cache total, 256 KB on each core)
•  RAM: 1 GB 533 MHz DDR2 RAM (2 x 512 MB)
•  Hard Drive: 120 GB Hitachi 5400 RPM HD
•  Screen: 14.1-inch WXGA Acer CrystalBrite screen
•  Gaphics: ATI Radeon Xpress 1100 integrated graphics (64-256mb shared memory)
•  Optical Drive: Dual layer DVD +/- RW combo
•  Wireless: Atheros Wireless 802.11 b/g with Signalup high efficiency antennae

I am able to get the splash screen of Ubuntu that give you the option to install but when I try to view live or even try to install Ubuntu It stops at a command prompt. It won’t install.
I had no issue’s installing Ubuntu on my son’s system, easy money, but this notebook has been a challenge. Anybody have any ideas why this is happening

Yes I am using the 64bit version. 

Steven

---

### Post by Pumalite on 2008-08-04
The SOLUTION is very simple:

- just add the option all_generic_ide to the grub boot option

---

### Post by dancingbear909 on 2008-08-06
What does this all mean?


(initramfs) [193.317254]8139cp 0000:08:02.0: this (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[193.317254]8139cp 0000:08:02.0: Try the "8139too" driver instead.

still having an issue installing Ubuntu on that notebook.

Steven

---

### Post by dancingbear909 on 2008-08-06
> **Pumalite said:**
> The SOLUTION is very simple:

- just add the option all_generic_ide to the grub boot option



This did not work. Sorry any other suggestions?

Steven

---

### Post by dancingbear909 on 2008-08-12
Still need help getting Ubuntu installed on my Acer 5050 notebook. 

Anybody:confused:

Steven

---

### Post by Pumalite on 2008-08-12
[http://ubuntuforums.org/showthread.php?t=632151&page=3](http://ubuntuforums.org/showthread.php?t=632151&page=3)

---

### Post by dancingbear909 on 2008-08-14
Pumalite thank you for all your help. I checked that thread out, plus I did a little more reading on GNU GRUB, I am not trying to multiboot my Acer I am trying to install 1 OS being Ubuntu as my primary OS. 


After I get to the install page where it gives you like 4 different option "Try Unbuntu with out installing" and so on, the system will act like it's going to in stall then it goes too a (initramfs) promp. 

So where do I go from here? 

Steven

---

### Post by Pumalite on 2008-08-14
Boot your Live CD and post:
sudo lshw

---

### Post by blogthis on 2008-08-21
I have the same issue.  The error comes up regardless of whether I try to install Ubuntu or just boot from the live CD.  

all_generic_ide didn't help

---

### Post by Circus-Killer on 2008-08-22
i have an aspire 5315, and everything works well, my only issue is that the clearbrite display is very dim. only thing stopping me from using ubuntu on it.

---

### Post by Pumalite on 2008-08-22
Try other boot parameters:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off  vga=0x317
One by o0ne or in different combinations.
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

---

