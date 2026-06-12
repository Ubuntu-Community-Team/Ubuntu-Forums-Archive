---
title: "Messed up grub on dual boot machine - how to repair?"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by almikul on 2011-12-13
Hi folks,

My question may sound familiar to many, but I believe my situation is a bit unique because I was not able to find a solution. I was given a work laptop with Win7 pre-installed. I decided to install Ubuntu 11.10 on an usb external hard-drive. My intention was to load Ubuntu when the external drive is present and load Windows when it is absent. After installing Ubuntu, I found out that grub works only when the external drive is present, so when it is absent - nothing will load. I thought that since grub was installed on the internal hard drive (sda), it would just ignore sdb when it cannot see it, but instead, it gives me an error. 

To make matters worse, I've tried to install grub manually on sda, and now it boots into grub command line. I need to resolve this problem and make Windows bootable  regardless of any other conditions. I really do not want to ask our work IT people for help because technically I was not supposed to modify the laptop's OS. 

What would you recommend? At this point, I reinstalled Ubuntu on the external drive and could finally load Windows startup repair. I hope I can repair the Windows bootloader and in the future launch Windows and Ubuntu completely separate (not dual boot).

Thank you.

---

### Post by BC59 on 2011-12-13
If you manage to reinstall MBR on Win7 with Windows startup repair (I think you have to try it at least 3 times to have success) then I propose as solution, to install Ubuntu through Windows, with Wubi.exe installation. Ubuntu is installed as another Windows program and you can uninstall it whenever you like with add/remove programs. 
The only visible difference is that when you boot the computer, Windows is presenting a screen to choose between the 2 systems.

---

### Post by almikul on 2011-12-13
Thank you for your suggestion, BC59. I could restore the Windows bootloader by creating the Repair DVD, and I am going to try Wubi.

---

