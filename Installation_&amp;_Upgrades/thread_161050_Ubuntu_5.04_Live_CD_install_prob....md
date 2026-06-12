---
title: "Ubuntu 5.04 Live CD install prob..."
date: 2006-04-16
forum: Installation &amp; Upgrades
---

### Post by canadiandude on 2006-04-16
Hi everyone,

I'm a complete noob to Linux but am seriously considering the switch from WinXP. A while ago, I ordered the Ubuntu 5.04 CDs and tried the Live CD which worked fine. 

However, when I try the Live CD now, it will install fine but always bring me to a blank brown screen with only the mouse curser showing. Nothing else. I don't want to go ahead with an install if I am going to get the same problem.

My thinking was initially that it did not like my widescreen LCD monitor having a 1440x900 resolution but now I think it may simply be the graphics card drivers. (although, it did work fine during the initial Live CD trial). Would 5.10 fix this problem or is that just grasping at straws?

Here are my system specs:

DFI Lanparty UT Ultra-D NF4 mobo
AMD X2 4200+ CPU
2GB Crucial Ballistix PC4000 RAM
Xpertvision NVidia 7800GT 256Mb vid card
160Gb Samsung Spinpoint SATA HD
250GB WD SATA HD
NEC 4571 DVD Burner w/ Labelflash
Floppy drive
Zalman 9500 CPU Cooler
Fujitsu-Seimens W19 monitor (widescreen)

Thanks in advance for any input!

---

### Post by Kapre on 2006-04-16
[QUOTE=canadiandude]Im a complete noob to Linux but am seriously considering the switch from WinXP. A while ago, I ordered the Ubuntu 5.04 CDs and tried the Live CD which worked fine. 

However, when I try the Live CD now, it will install fine but always bring me to a blank brown screen with only the mouse curser showing. Nothing else. I don't want to go ahead with an install if I am going to get the same problem.

My thinking was initially that it did not like my widescreen LCD monitor having a 1440x900 resolution but now I think it may simply be the graphics card drivers. (although, it did work fine during the initial Live CD trial). Would 5.10 fix this problem or is that just grasping at straws?

Thanks in advance for any input![/QUOTE]

CanadianDude - I dont think it is the problem with your monitor, most probably (but not sure) it is your grfx card. I would assume you have a hi-speed connection to the internet. Try cleaning the CD (install) first (wipe it clean) then reinstall. If the same problem occurs, try doing the "server" install then follow this link from the Ubuntu Docs up to the "sudo apt-get update" only. Then after that, enter "sudo apt-get install kubuntu-desktop" and if for some reason the same problem occurs, enter "dpkg-reconfigure xserver-xorg" (to reconfigure the card and resolution".

Post again if you have another problem.

K

---

