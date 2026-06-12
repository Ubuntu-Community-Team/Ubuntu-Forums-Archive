---
title: "login:  [    25.260000] bcm43xx:  Error:  Microcode &quot;bcm43_xx_microcode5.fw&quot; not avai"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by nineowls on 2007-10-26
i was exploring getting working sound, getting working wireless, and doing miscellaneous things from an Ubuntu hacks book (on an otherwise perfectly functional 2.6.20-15 that i upgraded to -16). Point is, i cannot isolate exactly what i did to break Feisty but after reboot

i get the following error (in recovery mode as well)
[    ##.128000] bcm43xx: Microcode "bcm43xx_microcode5.fw" not available or load failed.
firmware_helper[4716]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:0c:00.0' with driver '(unknown)'

Per following post:  Microcode "bcm43xx_microcode4.fw" Error
I have in recovery mode and as root@mymachine: modprobe -r bcm43xx
I have in recovery mode and as root@mymachine: sudo modprobe -r bcm43xx
init 2 
still hangs  hangs
reboot into recovery
vi gedit /etc/modeprobe.d/blacklist
(added to end)
blacklist bcm43xx

NOW: my -16 kernel and my (-16 recovery)  and my -15 kernel and my (-15 recovery)
all go to tty1
machinename login: invalid login
init 5
hangs at : "Running local boot scripts (/etc/rc.local)"
Ctrl+alt+del
GOTO NOW

on break: anyone have any suggestions? 
i could try logging in with the cd and backing up my stuff to the network and installing Gutsy, but you smart people may know an easier, kinder command. 

Thanks in advance...

---

### Post by nineowls on 2007-10-31
so--first of all--as there was no comment I have deleted exisitng 7.01 install and after partitioning a large ext3 /home, installed 7.10

everything works beautifully

I discovered prior error was related to proprietary wireless card, which are readily and easily available in Gutsy

---

