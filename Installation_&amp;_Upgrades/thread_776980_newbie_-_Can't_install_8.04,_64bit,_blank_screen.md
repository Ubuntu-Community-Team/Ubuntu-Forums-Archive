---
title: "newbie - Can't install 8.04, 64bit, blank screen"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by AussieLes on 2008-05-01
The following occurs in both Full install or with live cd. When running the install at boot I see the original screen and select English. I then see the black, installing kernal screen, after this the first orange screen fails to appear and my monitor goes blank. My DVD drive continues to run and my floppy drive runs a couple of times. It appears that my system is running the install but as I can't see it, i can't enter the screens to input options. Now i am a complete noob to Ubuntu so any help would be greatly appreciated. Unfortunately need to dual boot with Vista due to some games and software I run. I want to trial\learn on smaller drive with view to replacing Vista at later date

MOBO - Gigabyte - GA-P35-DS3P
CPU - Intel Q6600 Quad core
RAM - 2GB Dual Channel
Video - 320mb 8800GTS
Hard Drives - 320Gb maxtor sata - Vista 32 bit
            -  80Gb Seagate IDE - Hopefully with Ubuntu
DVD Drive - LG - can't remember model but is working normally

---

### Post by njparton on 2008-05-01
You need to hit F6 on the first options screen and remove the bit that says "splash" (or change it to "nosplash" without the quotes).
 
Try that. If that doesn't work write down what other commands are present after pressing F6 and post them back here.
 
You could also try installing in safe graphics mode, that should be another option.
 
The 3rd option is to install using wubi by opening the CD under Vista.

---

