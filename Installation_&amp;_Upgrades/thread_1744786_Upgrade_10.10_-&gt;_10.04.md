---
title: "Upgrade 10.10 -&gt; 10.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Fire-EnigmaX on 2011-04-30
I had been running 10.04, then upgraded fine to 10.10 before being offered the upgrade to 11.04 which I did... 

Everything seemed to go OK (although the upgrade to 11.04 took a LONG time but eventually did complete.. but when the laptop rebooted I get the screen flickering blank duing boot and eventually it stops with the following:

* ... {various starting/stopping messages all showing status of [OK]}
* modprobe vboxdrv failed. please use 'dmesg' to find out why
* ... {various starting/stopping messages all showing status of [OK]}
* Checking battery state...               [OK]

and it then fails to load any further. 

I can start using the liveCD fine without problems.

I'm not sure what other information to provide here (please advise) to make things easier/better for you to work out what's wrong..

I'm not sure what else to do (still much a noob with linux) 
(I really don't want to have to re-install unless absolutly necessary)

Any help would be great
Chris

---

### Post by Rubi1200 on 2011-04-30
Hi,

please post the specifications for the laptop, especially graphics card and RAM.

---

### Post by Fire-EnigmaX on 2011-04-30
Sorry...

Dell Studio 1555
The following specs apply (taken form order summery from dell site):

N1053503
STUDIO 1555 : PENTIUM DUAL CORE T4300(2.
DISPLAY : 15.6IN WIDESCREEN HIGH DEFINIT
PALMREST : STANDARD
CAMERA : INTEGRATED 2.0 MEGA PIXEL CAMER
LCD BACK COVER : MIDNIGHT BLUE MICROSATI
SHIP ACCESSORY : ENGLISH DOCS
RESOURCE DVD : STUDIO 1555 DIAGNOSTICS A
MEMORY : 4096MB (2X2048) 800MHZ DDR2 DUA
HARD DRIVE 320GB SATA (5400RPM)
OPTICAL DRIVE : 8X DVD+/-RW DRIVE INCLUD
POWER SUPPLY : INSPIRON 90W AC ADAPTER
POWER CORD : UK 1M
MODULE..., BATTERY..., PRIMARY..., 56WHR, 6C, SANYO
GRAPHICS : 512 MB ATI MOBILITY RADEON? H
WIRELESS : DELL WIRELESS 1397 (802.11 B/
WIRELESS LABEL - PENTIUM DUAL CORE
MOBILE BROADBAND : DELL WIRELESS 5530 CA
KEYBOARD : INTERNAL UK/IRISH QWERTY KEYB
STUDIO 1555 ORDER - UK
STUDIO NB - SYSTEM ONLY

---

### Post by lechien73 on 2011-04-30
Could you try selecting "Recovery Mode" from the GRUB menu on boot? If you can't see the GRUB menu, then hold down the Shift key while starting up the computer.

When you have selected "Recovery Mode", then choose "Failsafe-X". Does Ubuntu now start? If so, then try reinstalling your graphics driver.

---

### Post by Fire-EnigmaX on 2011-05-01
Thanks,

I started into FailSafe-X and was able to launch the driver manager and activate the graphics card driver.

When doing this it gave an error 

"System Program Problem" 
_do you want to report the problem now?_

Then I got an error saying 

"Sorry the package "virtualbox-3.2" failed to install or upgrade"
_ you can help the developers to fix...
(Clicking on report problem produces a message that it cant be reported because its not a genuine ubuntu package .."

However after a reboot to finish activating the driver, the laptop boots into ubuntu fine again (into 11.04).


Many thanks for your help.
Chris

---

