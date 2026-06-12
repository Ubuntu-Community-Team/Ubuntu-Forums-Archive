---
title: "Please help - problem with boot"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by DanM on 2005-07-04
First of all I am new-newbie and my English is not very good so … please be kind with me!
Thank you for Ubuntu CD’s! I’ve just finished giving CD’s to all my friends and they enjoy it.
But I have a big problem with Linux. 
I have a computer with the following configuration:
CPU INTEL Pentium 4/3 GHz
MB ASRock P4I65GV/ video on board Intel 82865G
512 MB DDRAM PC3200
HDD SATA 120 GB 7200 RPM
DVD-ROM TOSHIBA
CR-RW TEAC
MODEM Intel 536EP, internal
First time when I have installed Linux was Suse 9.1 Pro. It went smoothly, no problems at all (I even managed to properly install the modem and navigate on Internet).
Then I bought a SPARKLE GeFORCE FX5500/350 MHz RAMDAC 128 MB DDR video card and the problem began. The system is freezing during boot.
I erased Suse Linux 9.1 Pro and put Mandriva 10.1 instead but the same problem occurred. I even try with KNOPPIX 3.7 PRO. When I choose to boot with kernel 2.6 freeze but when I boot with kernel 2.4 the system boots well, but video card is not recognized (manufacturer NVIDIA type unknown … ).
With Ubuntu Live the boot process goes well until * Starting hotplug subsystem …and freeze.
Please help me to install Ubuntu Linux on my computer (I wonder why Linux doesn’t recognize all the hardware with generic drives and then let the user to install the right ones to avoid problems like this. I have WindowsXP SP2 on other partition and is going fine).

Thank you for your help!

Dan Micu

---

### Post by al7kz on 2005-07-04
Bonjour,

I never could get Mandrake 10.1 or Knoppix  to install either. Try installing Ubuntu Hoary with the install cd. Use boot option agpgart. I had to use that plus a lot of others - hit F2 during boot to see the list. 

The nvidia drivers aren't in most distros due to copyright issues. You can download the drivers from the nvidia site. 

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

On initial install or if you run xorgconfig choose the generic nvidia driver nv or vesa. Then install the nvidia drivers and change "nv" or "vesa" in xorg.conf to "nvidia".  Check the Hoary 5.04 Starter Guide on how to install the drivers.

mb Abit NF7-S2G, Sempron 2800+, 512MB Corsair VS, LeadTek 5200FX 128mb, 120GB WD SATA

Good luck!

al7kz

---

### Post by DanM on 2005-07-05
Thank you!

I'm going do to the instalation now...

DanM

---

### Post by pijamab on 2006-05-09
I'm having the same problem with Dapper Drake flight 6 Beta2.  It boots correctly until about when the "hotplug subsystem" comes up then the display tries to switch twice and goes black with the backlight still on.  I have a [Linux Certified LC2100]("http://www.linuxcertified.com/linux-laptop-lc2100.html").  Breezy 5.10 works perfectly, and I have reverted.  I'm very happy with 5.10, but I hope this issue can be addressed before the official Dapper Drake release is set.

PS Keep up the great work!  Ubuntu is the shiznit.

---

