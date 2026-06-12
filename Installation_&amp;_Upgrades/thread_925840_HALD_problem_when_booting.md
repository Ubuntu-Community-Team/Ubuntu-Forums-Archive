---
title: "HALD problem when booting"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by theojepsen on 2008-09-21
I got an alternate installation CD of Ubuntu 8.04 and installed it on my computer. I partitioned a 250GB hard-drive so that it has a Windows partition (it works), an Ubuntu partition and a 1GB partition for swap.

When I boot normally the progress bar just freezes at around 90%. When I hit alt+ctrl+F1, I see that it gets stuck at this:

"* Starting Hardware abstraction layer hald	_"

When I boot in recovery mode and drop the root shell prompt I type:

"/etc/init.d/dbus start"
"/etc/init.d/hal start"
"/etc/init.d/gdm start"

This brings me to the usual Ubuntu GUI and I am able to log in and do most things that I would like to do on Ubuntu (office, gimp, music, etc.). Not only would I like to boot normally, without using the root shell every time, but the wireless card and the and graphics are not working properly: the wireless card is detected, can find networks, but can't connect. The graphics card is not detected at all (I had to edit the xorg.conf just to get it to load the GUI properly).

My system specs are:

Asus M2V-MX motherboard
AMD X2 3800+
2GB RAM
250GB HDD
GeForce 9600GT

I managed to run Ubuntu before, until I swapped the my old ATI 1650 PRO for the GeForce 9600GT, therefore I think the GeForce is causing the problems.

Could somebody please tell me how I could get it working well like it did all the other times I installed it? Or should I just wait a few days for the next release and hope it solves the problems?

Thank you

---

### Post by theojepsen on 2009-01-31
I managed to boot without recovery mode by adding acpi=off to the boot parameters. Then I downloaded the latest Nvidia driver for my GeForce and ran sudo sh <driver>.run. Wireless works too.

---

