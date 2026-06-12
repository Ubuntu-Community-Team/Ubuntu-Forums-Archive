---
title: "Problem installing Ubuntu in ASUS PC with H410M-E motherboard"
date: 2021-03-13
forum: Installation &amp; Upgrades
---

### Post by fredson96 on 2021-03-13
So, here's the issue ;-;

I'm currently trying to install Ubuntu 18.04 or 20.04 (I'm trying both since I'm fine with either one, but failing miserably) in a PC with:

* [COLOR=#000000][FONT=lato] ASUS motherboard[/FONT][/COLOR] [COLOR=#000000][FONT=lato]Biostar H410MH DDR4 Socket LGA1200 Chipset Intel H410
* memory [/FONT][/COLOR][COLOR=#000000][FONT=lato]Memoria Crucial Ballistix 8GB (1x8) DDR4 3000Mhz Red, BL8G30C15U4R
[/FONT][/COLOR][COLOR=#000000][FONT=lato]* GPU [/FONT][/COLOR][COLOR=#000000][FONT=lato]Afox Radeon R5 220 2GB 64-bit, AFR5220-2048D3L9-V2
[/FONT][/COLOR][COLOR=#000000][FONT=lato]* storage [/FONT][/COLOR][COLOR=#000000][FONT=lato]HD WD Blue 1TB 3.5" Sata III 6GB/s, WD10EZEX
[/FONT][/COLOR][COLOR=#000000][FONT=lato]* [/FONT][/COLOR][COLOR=#000000][FONT=lato]Intel Core i5-10400F Hexa-Core 2.9Ghz (4.3Ghz Turbo) 12MB Cache LGA1200, BX8070110400F[/FONT][/COLOR]

As instructed in may online guides, I've disabled the fast boot and the secure boot (i.e., I cleared the keys and selected "Other OS"; now, the "Secure Boot state" is "setup", which I assumed is equivalent, but please tell me if it isn't) in BIOS. I've also tried to add "nomodeset" and "nouveau.modeset=0" after "quite splash" after pressing "e" on the GRUB window. However, despite this efforts, the installer keeps crashing. I've no idea of what to do now. Anyone can give me a hand, please?

---

### Post by CelticWarrior on 2021-03-13
Please describe the crash.

---

### Post by fredson96 on 2021-03-13
After selecting language, time zone, etc., the installer starts to work. It goes through some step, like copying images, etc. However, during the "Detecting hardware, please wait" step, it crashes with the message "INSTALLER CRASHED  We are sorry; the installer crashed. After you close this window, ... as soon as possible." As you can see, a very blunt error message, without specifying the reason or anything like that. Maybe worth noting: I've selected minimal installation, and have tried with wi-fi connection and without it.

---

