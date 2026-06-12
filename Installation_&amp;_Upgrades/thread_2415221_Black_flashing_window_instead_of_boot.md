---
title: "Black flashing window instead of boot"
date: 2019-03-22
forum: Installation &amp; Upgrades
---

### Post by marv123123123 on 2019-03-22
[COLOR=#1D2129][FONT=Helvetica]Hi guys! I'm having a really weird problem.[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]I'm making a dual boot (windows 10 and ubuntu 16.04.6). My OS base is Windows 10. When I tried to install ubuntu for the first time, I had a problem with a black screen. I solved it using "noveau.modeset=0".[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]The problem is that I've already installed Ubuntu, however, it doesn't boot, even using "nomodeset", "nouveau.modeset=0", "acpi=off", "no splash", etc. Sometimes, my screen just turns black and flashes. And sometimes the message "The system is running in low-graphics mode" pops up, but the options do nothing.[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]I have a ThinkpadP52, NVIDIA Quadro P1000[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]PLEASE HELP!![/FONT][/COLOR]

---

### Post by oldfred on 2019-03-22
If nVidia, you need nomodset set on first boot or until you install the nVidia driver from Ubuntu's repository or the Ubuntu ppa for newer drivers.
If you can boot to terminal with recovery boot option, second or third in grub menu, then you can use terminal to install driver.

       nVidia install, purge if needed.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

---

