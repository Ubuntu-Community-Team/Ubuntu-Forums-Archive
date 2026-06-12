---
title: "install and upgrade woes"
date: 2015-05-01
forum: Installation &amp; Upgrades
---

### Post by night116 on 2015-05-01
I have a Toshiba Qosmio
Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
800.000 MHz
memory 32349mb
network controller:
intel dual band wireless AC 7260
ethernet contoller: qualcomm atheros AR8161 gigabit ethernet rev10 
sdc1 227Gb : my / root partition
sdb1 917Gb : my /home2 partition
sda1 917Gb : my /home partition 

I tried to install from a fresh copy of ubuntu 15.04 but in no way will it boot, it just keeps freezing, and on the one occasion when I did get to the install process, once it rebooted it just kept on freezing.

I then reinstalled the only version I could get to boot without freezing was 14.04,then with huge problems upgraded to what it states as 14.10 using linux 3.13.0-49 generic, which I have to press the shift key to get as the other ones do not work and the computer just freezes every time on boot.

please can someone shed some light on what t do

---

### Post by night116 on 2015-05-01
i also tried to upgrade from 14.10 and the same thing happens after the upgrade.

---

### Post by kc1di on 2015-05-01
The one piece of information we are missing is what video card is the machine using?  freezes on boot are normally traced to the video driver.

---

### Post by night116 on 2015-05-01
i also tried to upgrade from 14.10 and the same thing happens after the upgrade.

---

### Post by night116 on 2015-05-01
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

### Post by night116 on 2015-05-01
this also freezes on using a live dvd of ubuntu any version except 14.04

---

### Post by night116 on 2015-05-01
thanks you pointed me in the right direction to fix this issue so far it was the video drivers causing it.
so far so good.

---

### Post by kc1di on 2015-05-01
Glad it's working for you. 
With nvidia cards you have to reinstall the driver for a new Kernel when you upgrade. 
enjoy :)

---

