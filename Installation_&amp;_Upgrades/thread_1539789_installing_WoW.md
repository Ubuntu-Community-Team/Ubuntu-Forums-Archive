---
title: "installing WoW"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by meksikan on 2010-07-27
i'm sorry as i'm sure this has been brought up, but i need some help. i'm pretty new to ubuntu and i need some help if anyone can. anyways.. here's my problem:

i was taking a look at the wow installation guide and am already having a problem with the very first thing that has to do with direct rendering. i typed the command it stated but it doesn't tell me anything and just starts a new line. next thing i tried was glxinfo and it says

name of display: :0.0
Segmentation fault

here's where i'm stumped, i have tried searching the forums but i don't think i've found the right solution as to enable direct rendering. i don't know if i have multiple video drivers installed that may be conflicting with one another or what. i have read about video cards being black listed from something called compiz but i don't know if that applies to my situation or not.

i have tried going to system>administration>hardware drivers, but nothing about video card drivers pops up there. the onlything that pops up on the list is for "broadcom b43 wireless driver."

i have also tried running the compiz command in terminal, but it said something about fatal errors or whatever. i'm sorry if i haven't provided enough info, but i'm just going based off what i can remember trying. i'm 70% certain of going back to windows just for gaming, even tho i would like not to.

**TL;DR**
i would like to play wow by enabling direct rendering, heh.

---

### Post by P4man on 2010-07-27
Sounds like your problem is the videodrivers. What videocard do you have? If you are unsure; open a terminal and type
```
lspci
```

and copy paste the output here.

---

### Post by meksikan on 2010-07-27
heres my result:

gabe@gabe-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:09.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller 2 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
02:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by P4man on 2010-07-27
that videocard (radeon 9600) is no longer supported by the proprietary ATI drivers. I have no idea how well the opensource drivers work, but at least I would think it should allow compiz. Are you running ubuntu 10.04 or an older version?

---

### Post by meksikan on 2010-07-27
10.04 Lucid 2.6.32-24-generic

---

### Post by P4man on 2010-07-27
Like i said; im not sure how well the oss ATI drivers work; but by default they should enable direct rendering and 3d acceleration. Have you tried installing proprietary drivers? If you have, or you are not sure; try reverting back to the oss drivers:

```
sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```

reboot; see if it helps. if it doesnt help; you could try adding this PPA with more updated drivers:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

To do that; open a terminal and paste this in:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
```

Then update your sources:
```

sudo apt-get update
```

and then upgrade to the new stuff:
```

sudo apt-get upgrade
```

after that reboot and see if you can get desktop effects working now.

But again; this ought to have worked without doing anything as the RV350 is supported out of the box.

---

### Post by meksikan on 2010-07-27
ill give it a go thanks. i'll edit this post with my results as to not double post.

Edit:

i tried the above and after trying to enable desktop effects, it said it could not be enabled. so would that mean installing the game would be useless?

---

### Post by P4man on 2010-07-27
> **meksikan said:**
> ill give it a go thanks. i'll edit this post with my results as to not double post.

Edit:

i tried the above and after trying to enable desktop effects, it said it could not be enabled. so would that mean installing the game would be useless?

Would be nice if you could tell us what output you got when you did all of the above. Did you get any errors?

Anyway, is this a fresh install or something you have been messing with? Id advice you to try a livecd (just boot the cd or usb stick you made to install ubuntu) and test desktop effects there (simply system > preferences > appearance > visual effects > maximum). If that works from a livecd then you probably messed something up and we should be able to fix it. 

If that doesnt work; then OSS drivers for your card have an issue and I will leave this thread to someone more knowledgable about ATI drivers on old ATI cards but it may take some dedication from your part to get it working properly.

---

### Post by meksikan on 2010-07-27
Its an upgrade from 9.10, which was a fresh install. so i dont have a live cd for 10.04. but i suppose i can format my drive and start fresh. 

i didnt receive any errors doing the steps you provided. thanks for your hard work. appreciate it.

---

