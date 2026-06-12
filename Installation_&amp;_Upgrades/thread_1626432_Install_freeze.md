---
title: "Install freeze"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by g-pita on 2010-11-20
I'v been trying to install Ubuntu (and actually all other dists of linux (in hope of succes), but running ubuntu on my other machines and prefer it) on my old laptop.

Laptop Acer Aspire 1312XC
Have just run a 24 hour RAM test it turned out ok.
Have tried with other RAM blocks in aswell.

The install freezes at random points in the installation.
Mainly when trying to copy files to the hard drive.

The only thing i've succeded in installing was Ubuntu server and windows XP.

I have tried with ACPI off and all the other special atributes.

No success so far.

---

### Post by Quackers on 2010-11-20
Welcome to UF :-)
Did you check the MD5SUM of the downloaded .iso file? This makes sure the download was not corrupted. See below

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Then if that's ok, you can check the cd itself by tapping F6 near the start(I think it is!)  and selecting the check disc option.

---

### Post by g-pita on 2010-11-28
Both tests turned out with out errors...

The only os's i've been able to put onto the machine are systems with textbased installers.
[LIST]
[*]FreeBSD,
[*]Ubunutu Server,
[*]Dahm Small Linux
[/LIST]
But i've tried all setup-flags at ubuntu.
:(

---

### Post by sikander3786 on 2010-11-28
Hi.

Are you sure your machine or the CD/DVD Drive is not overheating? Is the CD/DVD drive ok?

Can you please list your hardware specs?

And if you've got a USB drive, I would suggest to use it as an installation media and see if that succeeds in the installation.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by g-pita on 2010-11-28
It is a rather old laptop so it cannot boot from USB :(
A Acer Aspire 1312XC,

but the cd-drive is ok - i've just been copying files from it for an hour in dahm small linux without any problems..

---

### Post by sikander3786 on 2010-11-28
> **g-pita said:**
> It is a rather old laptop so it cannot boot from USB :(
A Acer Aspire 1312XC,

but the cd-drive is ok - i've just been copying files from it for an hour in dahm small linux without any problems..
Other hardware specs please. Specifically RAM...

---

### Post by g-pita on 2010-11-28
Processor AMD Athlon XP-M 2000+ / 1.67 GHz
Data Bus Speed 266.0 MHz
Chipset Type VIA ProSavageDDR KN266
Cache Memory
Type L2 cache
Installed Size 256.0 KB
RAM
Installed Size 256.0 MB / 2.0 GB (max)
Technology DDR SDRAM - 266.0 MHz
Memory Specification Compliance DDR266/PC2100
Form Factor SO DIMM 200-pin
Storage Controller
Storage controller type IDE
Storage
Floppy Drive 3.5" 1.44 MB floppy - Integrated
Hard Drive 30.0 GB
Storage Removable None
Hard drive type Portable
Optical Storage (2nd)
2nd optical storage type None
Optical Storage
Type CD-RW / DVD-ROM combo - Integrated
Read Speed 24x (CD) / 8x (DVD)
Write Speed 24x
Rewrite Speed 10x
Display
Display Type 14.1 in TFT active matrix
Max Resolution 1024 x 768 ( XGA )
Widescreen Display No
Color Support 24-bit (16.7 million colors)
Video
Graphics Processor / Vendor AGP 8x - S3 ProSavage8 Shared video memory (UMA)
Audio
Audio Output Sound card
Compliant Standards DirectSound
Audio Input None
Input Device(s)
Input device type Touchpad , Keyboard , Scroll button
Telecom
Modem Fax / modem
Max Transfer Rate 56.0 Kbps
Protocols & Specifications ITU V.90
Networking
Networking Network adapter
Data Link Protocol Fast Ethernet , Ethernet
Expansion / Connectivity
Expansion Bays None
Expansion Slots Total (Free) 2.0 ( 1.0 ) x Memory - Type II/III , 1.0 ( 1.0 ) x CardBus - SO DIMM 200-pin
Interfaces 1.0 x IEEE 1394 (FireWire) - IEEE 1284 (EPP/ECP) - RJ-11 , 2.0 x Network - Ethernet 10Base-T/100Base-TX - 4 pin USB Type A , 1.0 x Microphone - VGA - 15 pin HD D-Sub (HD-15) , 1.0 x Display / video - Phone line - Mini-phone 3.5 mm , 1.0 x Headphones - Input - RJ-45 , 1.0 x Display / video - S-video output - Mini-phone stereo 3.5 mm , 1.0 x Hi-Speed USB - Output - 25 pin D-Sub (DB-25) , 1.0 x Parallel - 4 pin mini-DIN , 1.0 x Modem
Compliant Standards ACPI
OS Provided Microsoft Windows XP Home Edition

I've added RAM so is has 768MB
I've also tried to replace the RAM with 2 other blocks 2x512 GB without any success.

And i've run the memorytest fro the ubuntu cd for 12H

---

### Post by sikander3786 on 2010-11-28
> RAM
Installed Size 256.0 MB / 2.0 GB (max)

[s]Not too good for Ubuntu.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I would suggest you better go for Lubuntu, an Ubuntu lightweight fork.

[http://lubuntu.org](http://lubuntu.org)[/s]

Sorry I missed the bottom part of your post :-)

So it has got 768 MB RAM now?

---

### Post by g-pita on 2010-11-28
> **sikander3786 said:**
> [s]Not too good for Ubuntu.

So it has got 768 MB RAM now?

Yes it has.

---

