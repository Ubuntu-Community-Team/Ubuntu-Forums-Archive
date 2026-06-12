---
title: "install issues"
date: 2015-06-19
forum: Installation &amp; Upgrades
---

### Post by night116 on 2015-06-19
I am trying to install ubuntu 14.10 and this also happens on installing 15.04, when I try to boot from dvd every time it locks up and I can never get to install it, or I try to live boot the same thing happens, I think it is due to my video card as it will boot into 14.04.
I have a Toshiba Qosmio
Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
800.000 MHz
memory 32349mb
network controller:
intel dual band wireless AC 7260
ethernet contoller: qualcomm atheros AR8161... 
description: 3D controller
product: GK106M [GeForce GTX 770M]
vendor: NVIDIA Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list rom
configuration: driver=nouveau latency=0

---

### Post by night116 on 2015-06-19
tried nomodeset
tried acpi=off

---

### Post by grahammechanical on 2015-06-19
Forget 14.10. It only had 9 months support and that is about to run out. Ubuntu 15.04 only has 9 months support as well. If you can install 14.04 then install that and then either

a) upgrade to 14.10 and then to 15.04 but use the open source video driver and keep the install close to a default install
or
b) continue using 14.04 and then upgrade to 16.04 next year.

There are three ways we can start the installer and there have been times when I have had to try all three of them to put in an install.

1) Let the live session run and at the Try - Install dialog click Install
2) Let the live session run and at the Try - Install dialog click Try and at the live session desktop click the Install Ubuntu icon
3) At the first purple screen press Enter. Select the Language (default is English) and press Enter. Then at the underlying text mode screen select Install Ubuntu.

Regards.

---

### Post by night116 on 2015-06-20
yeah thanks, I had to install 14.04 as it was the only one to boot then changed the video settings but did not reboot, then upgraded to 14.10, rebooted with the new settings and now upgrade to 15.04.
no other choice would work due to video settings freezing any other dvd live or install.

---

