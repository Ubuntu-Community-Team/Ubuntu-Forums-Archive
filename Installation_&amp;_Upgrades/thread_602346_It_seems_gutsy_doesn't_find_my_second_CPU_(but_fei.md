---
title: "It seems gutsy doesn't find my second CPU? (but feisty did!)"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Adnarim on 2007-11-04
Hi,
I have a really weired problem here. I'm on a Toshiba Satellite A100-773 and using gutsy with 2.6.22-14-386. If I now check the acpi thermal zones I get:
> 
$:watch -n 1 acpi -V

Every 1,0s: acpi -V                                     Sun Nov  4 11:07:15 2007

  Battery 1: charged, 100%
  Thermal 1: ok, 59.0 degrees C
  Thermal 2: active[0], 58.0 degrees C
  AC Adapter 1: on-lin


What's really weired because one is labeled as ok and the other as active[0] ?? 

Then If I wanna change the scaling governor of the cpu:
> [11:08:50]bash:/sys/devices/system/cpu$ dir
cpu0

There's just one cpu listed? This seems as the second one is not recognized or am I wrong? What could be the problem/cause and how to solve it?

greets

---

### Post by dcstar on 2007-11-04
> **Adnarim said:**
> Hi,
I have a really weired problem here. I'm on a Toshiba Satellite A100-773 and using gutsy with 2.6.22-14-386. If I now check the acpi thermal zones I get:


What's really weired because one is labeled as ok and the other as active[0] ?? 

Then If I wanna change the scaling governor of the cpu:


There's just one cpu listed? This seems as the second one is not recognized or am I wrong? What could be the problem/cause and how to solve it?

greets

386 kernels do not support SMP, install the -rt or -generic kernels.

---

### Post by Adnarim on 2007-11-04
Hi,
thanks this worked for me :) But unfortunatly I can't get no wlan anymore with the generic kernel.

I have an ipw3945 card. I updated from feisty to gutsy and had to install the package linux-ubuntu-modules-2.6.22-14-386 to get my wlan-running. Now with the generic-kernel this doesn't work but the linux-ubuntu-modules-generic package has already been installed.

iwconfig doesn't list my wlan-device with the generic kernel and dmesg | grep ipw shows:
> 
[11:54:36]bash:~$ dmesg | grep ipw
[   19.392000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   19.392000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.392000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   22.704000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   59.736000] ipw3945: association process canceled


Any idea?

---

