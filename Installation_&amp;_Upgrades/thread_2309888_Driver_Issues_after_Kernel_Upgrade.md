---
title: "Driver Issues after Kernel Upgrade"
date: 2016-01-14
forum: Installation &amp; Upgrades
---

### Post by eagledrc2 on 2016-01-14
Hello all,

I just installed Ubuntu 14.04 LTS on my new Dell XPS 9550 laptop. I'm dual-booting with Windows 10. I had a lot of problems installing it with the UEFI and SSD but I figured those out. After starting it for the first time everything worked well (just like it did on the live USB), WiFi, screen brightness, etc. I ran apt-get update and was prompted by the GUI to install some Ubuntu updates and those required a reboot. Before I rebooted, I also installed a driver for my Targus 3.0 USB dock. As soon as I installed the driver, the secondary monitor (which wasn't working before the driver), started working then the computer froze. The keyboard didn't work at all neither did the mouse (usb mouse or trackpad). I rebooted and the WiFi wasn't working. My USB drive wasn't working when I plugged it in. I installed a .deb file for my Broadcomm WiFi (I had been told that the WiFi wouldn't work so I had this file handy). After installing the .deb file the WiFi still didn't work. I can't find much about this online and I'm stumped. 

The kernel that came with 14.04 was 3.13. The upgrades took me to 3.16. I tried booting back to 3.13 through GRUB and the issues were the same. I've tried re-installing Ubuntu through the live USB and it freezes after selecting the options (download updates while installing, install MP3 codecs) every time (tried 4-5 times). Does anyone have any tips? I'm about to give up on dual-booting Ubuntu with Windows 10 if I can't figure this stuff out. I ran several dual-boots several years ago and never had problems like this.

---

