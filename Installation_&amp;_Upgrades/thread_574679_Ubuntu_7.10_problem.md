---
title: "Ubuntu 7.10 problem"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by lavinia on 2007-10-13
Hello.
I download ubuntu 7.10 rc 64 bit.

but install screen black. but after 2 minute displaying desktop. 

after click to install icon. ok no problem. 
after reboot. (black screen.)

after start black screen and booting says: kernel alive... but after 1 minute login screen..


My hardware:

Processor:
DualCore AMD Athlon 64 X2, 2600 MHz (13 x 200) 5000+

Mainboard:
Asus M2N  (3 PCI, 2 PCI-E x1, 1 PCI-E x16, 4 DDR2 DIMM, Audio, Gigabit LAN)
(UBUNTU INCLUDED : Deficient)

Mainboard Chipset:
nVIDIA nForce 6100-430, AMD Hammer
(UBUNTU INCLUDED: ? )

BIOS:
AMI (01/12/07)

DISPLAY:
NVIDIA GeForce 8500 GT  (512 MB)
(UBUNTU INCLUDED: No )

MONITOR:
Philips 170S  [17" LCD]  (AU  013629) 170S7FB/00
(UBUNTU INCLUDED: No )

SOUND ONBOARD:
Analog Devices AD1988 @ nVIDIA MCP61 - High Definition Audio Controller
(UBUNTU INCLUDED: ? )

HDD:
SAMSUNG HD321KJ  (320 GB, 7200 RPM, SATA-II)

LAN ONBOARD:
NVIDIA nForce Networking Controller  (10.0.0.7)
(UBUNTU INCLUDED: Yes )

RAM:
DDR-II 667 1024 Kingston

Please help me and fix to included ubuntu 7.10 stable release...

---

### Post by lavinia on 2007-10-13
:confused: :(

---

### Post by Pumalite on 2007-10-13
Follow this guide: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Make sure you do md5sum on iso, burn at 4x. If 64 bit doesn't work; try 32 bit.

---

### Post by lavinia on 2007-10-13
:)

thanks for reply.

I download before 3 hour (32bit)..

but releated(some) problem. 

Writing with nero. 
( writing speed 4x and 32x and 52x.) 
cd check: no problem found. 


Please help me..


I understand.
Ubuntu 7.10 does not support my hardware :(

---

### Post by picopir8 on 2007-10-13
At grub, edit the boot command to remove the splash. There is a bug with the splash in the 64 bit version.

---

### Post by lavinia on 2007-10-13
> **picopir8 said:**
> At grub, edit the boot command to remove the splash. There is a bug with the splash in the 64 bit version.

Hmmm. thanks.

:popcorn:


 Trying...

"--splash" line remove ? 
or only "splash" ?

thanks.

---

### Post by Davix on 2007-10-19
Hi I m having the same problem, downloaded yestrday and everything went ok until the first rebbot, it took 3 mins ti get  the desktop, it is a black screen during 3mins or more..

Mine is a decent machine.

Thinkpad T43 1,86 Mhz
2GB ram
ATI X300

Any help!?

---

