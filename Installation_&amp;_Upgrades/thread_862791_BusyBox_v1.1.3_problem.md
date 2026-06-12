---
title: "BusyBox v1.1.3 problem"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by Ibrahim Mohammed Abdu on 2008-07-17
Hi, i have problem loading my Ubuntu 8.04 the following message keep showing on my screen.
BusyBox v1.1.1.3 (Debian 1.1.1.3 ubuntu12)Built in shell.enter "help" for a list of built in commands. pls. somebody help me.

---

### Post by Ibrahim Mohammed Abdu on 2008-07-17
:guitar:Hi, i have problem loading my Ubuntu 8.04 the following message keep showing on my screen.
BusyBox v1.1.1.3 (Debian 1.1.1.3 ubuntu12)Built in shell.enter "help" for a list of built in commands. pls. somebody help me.[/QUOTE]

---

### Post by overdrank on 2008-07-17
> **Ibrahim Mohammed Abdu said:**
> :guitar:Hi, i have problem loading my Ubuntu 8.04 the following message keep showing on my screen.
BusyBox v1.1.1.3 (Debian 1.1.1.3 ubuntu12)Built in shell.enter "help" for a list of built in commands. pls. somebody help me.

HI and please do not make multiple threads on the same issues
[http://ubuntuforums.org/showthread.php?t=862767](http://ubuntuforums.org/showthread.php?t=862767)
How did you install Ubuntu? What are system specs? A little more info would help.

---

### Post by David.Vodafone on 2008-07-27
I also have this same problem... i even reinstalled ubuntu and once i ran apt-get upgrade and restarted it was back again.

System Specs
Intel C2D E8400 3.0ghz
4GB Ram
ati HD3870
bluetooth dongle

---

### Post by David.Vodafone on 2008-07-27
i tried to startup without quiet splash and it stops on

[  35.834844] usbcore: registered new interface driver usbhid
[  35.834872] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

i can only think this would be my usb bluetooth dongle. but i installed ubuntu with it plugged in and i had rebooted with it before i ran apt-get upgrade

---

### Post by David.Vodafone on 2008-07-27
5 minutes later i think it passed the usb hid device.

it then came up with

Check root= bootarg cat /proc/cmdline 
or missing modules,devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/114d8b74-9cc3-42cd-83c4-55b130b269c1d does not exist. Dropping to a shell!

then we get into the busybox prompt.

---

