---
title: "SLOW boot from usb harddisk"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by palomar on 2008-07-25
Hi,
I installed Ubuntu on a usb harddisk on my desktop pc. Tested and it boots fine and quickly on my desktop. Then I plugged in the usb disk in my laptop. It starts booting, but it goes very slow in the beginning. Bringing up grub loader takes 30 seconds, then 30 seconds a blinking cursor, then black screen and suddenly the disks begins rattling quite loud and it starts booting at regular speed. Then it just takes one minute or something and Ubuntu is running fine. Running hdparm -t /dev/sda gives 14MB/s, which I think it's ok.

But... how do I solve that slow booting? It seems like the first boot stage is usb 1.0 speed or slower. It only occurs on this laptop. My desktop and other (more recent) laptop boot up quickly with that usb disk.

The laptop is a 2003 Targa Visionary XP10 with Athlon mobile xp 2500 and some kind of via chipset (how can I check this?). Internal hard drive and dvd drive have been removed.

---

