---
title: "Ubuntu 14.04 boots into tty1"
date: 2014-11-04
forum: Installation &amp; Upgrades
---

### Post by Lukas_Carls on 2014-11-04
Today I ran the Software Updater and rebooted my system. When it booted back up, it went up to the tty1 prompt. I tried hitting Ctrl+Alt+F7 to login through tty7, but to no avail. Consequently I logged in to tty1 and typed 'startx'. That loaded up the graphical desktop...without Unity. I hit Ctrl+Alt+T to start a terminal and I typed 'unity' to start it. The Launcher appeared but the panel was blank, so I typed 'gnome-panel' in another terminal. Now I can roughly work on my desktop, but I would much prefer to boot straight to the graphical realm and avoid all this hassle. I'm using this machine for my schoolwork, so any sort of help is appreciated!

Here is my setup:
Toshiba Tecra A8
Integrated Intel graphics
(I can provide other hardware stats if needed :KS)

Thanks! :D

---

### Post by Lukas_Carls on 2014-11-05
I used the GUI to find out what was being used for graphics, and it was the default Linux video driver, not the Intel driver that had been used before things went haywire. I also discovered that there was no audio. Hope this additional info helps. Thanks!

---

