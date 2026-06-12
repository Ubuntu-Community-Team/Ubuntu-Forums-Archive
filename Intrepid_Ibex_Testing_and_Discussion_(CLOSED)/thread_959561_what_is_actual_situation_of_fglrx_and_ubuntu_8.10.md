---
title: "what is actual situation of fglrx and ubuntu 8.10?"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by perriccolo on 2008-10-26
Hello. I've used serach and i found some information, but actual situation is not ok (in my mind :) ).

I've installed latest release candidate of ubuntu and kubuntu 8.10. But i did not find fglrx deb in repositories... In internet someone told me that i can not use fglrx on actual ubuntu. Is it correct? Is there some problem?

sorry for my bad english

---

### Post by sdowney717 on 2008-10-26
yes fglrx release is a beta from ATI.
I am running this right now and it is working on an x1300
the system shows it under menu system-admin-hardware drivers

some people posted this does not work on 9600 9700 etc... and that is true for me as well.

it works fine on an x1300
a 9600 ati card gives me no devices detected ubuntu runs in low graphics mode.

---

### Post by ktp on 2008-10-26
been running also and seems to be ok. Video playback can be better but this is not new.

---

### Post by Merovius on 2008-10-26
I personally could not get it to work with an x1650 Pro card. Went back to Nvidia 6800XE and everything is smooth as glass. 

I would really like to be able to use the ATI card at some point.

On the other hand, my son in law has an ATI X850 card that is running OK with occasional glitches.

---

### Post by perriccolo on 2008-10-26
> **sdowney717 said:**
> yes fglrx release is a beta from ATI.
I am running this right now and it is working on an x1300
the system shows it under menu system-admin-hardware drivers

some people posted this does not work on 9600 9700 etc... and that is true for me as well.

it works fine on an x1300
a 9600 ati card gives me no devices detected ubuntu runs in low graphics mode.

> **ktp said:**
> been running also and seems to be ok. Video playback can be better but this is not new.


i do not see any "fglrx" package in my repository. Must i enable some extra repository to have fglrx beta driver?

My module for proprietary driver find NOTHING. I've a x1950pro

---

### Post by ktp on 2008-10-26
[http://packages.ubuntu.com/intrepid/xorg-driver-fglrx](http://packages.ubuntu.com/intrepid/xorg-driver-fglrx)

---

### Post by perriccolo on 2008-10-26
> **ktp said:**
> [http://packages.ubuntu.com/intrepid/xorg-driver-fglrx](http://packages.ubuntu.com/intrepid/xorg-driver-fglrx)

thank you... now i download it.

But is strange... I don't have it DEB in adept or synaptic

---

### Post by ktp on 2008-10-26
do you have retricted enabled in software sources?  It needs to be enabled.

---

### Post by wgrant on 2008-10-26
You should always install proprietary drivers through System->Administration->Hardware Drivers.

---

### Post by jfelts on 2008-10-26
I can confirm it is not working on a 9600. Driver simply does not detect the card.

---

### Post by forger on 2008-10-26
*edited*

---

### Post by sdowney717 on 2008-10-27
yes they dont work on 9600 for me either

so will that ever be fixed?
does it work for anyone at all with an ATI 9000 series card?

from the link posted earlier it is supposed to be supported, but for me and others it does not work.
(I get no devices detected errors)

Video driver for the ATI Radeon and FireGL graphics accelerators.

This version of the ATI driver officially supports:

 * RADEON X1300, X1600, X1800, X1900
 * RADEON 8500, 9000, 9100, 9200, 9500, 9550, 9600, 9700, 9800
 * RADEON X800, X700, X600, X550, X300 series (AGP and PCI Express)
 * MOBILITY RADEON 9000, 9200, 9600, 9800, X700
 * MOBILITY RADEON 9000/9100 IGP Series
 * FireGL 8700, 8800, E1, E2, X1, X2, X3, Z1, T2
 * MOBILITY FireGL 9100, T2
 * RADEON XPRESS 200

. This package provides 2D display drivers and hardware accelerated OpenGL.

---

### Post by perriccolo on 2008-10-27
ok i've installed fglrx driver. 

Thank you.

"hardware driver" tells me that amd/ati proprietary driver is in use...

But... I've same speed problem that i had before installed proprietary driver....


I use kubuntu 8.10 updated this morning... How can i verify that i'm using fglrx driver? Is there some configuaration files? IMHO kubuntu are still using open driver and not fglrx

this is my xorg.conf

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```

---

### Post by jtuchscherer on 2008-10-27
Hi sdowney717,

I have trouble with my Radeon Mobility 9600 in Intrepid as well, but not only with the fglrx but also with the radeon driver. In both cases I get the error message before gdm starts with the offer to start the system in low graphics mode. Right now I can only use the vesa driver.

Do you have your system running fine with the radeon driver? If so, could you please share your xorg.conf?

Thanks,
Johannes

---

### Post by sdowney717 on 2008-10-27
well, I removed all entries from xorg.cong and was able to get 1024 by 768 with the free ati driver.
it will simply boot up without the 'no devices detected' or the low graphics message.
You dont know how much I hate seeing video problems and never seems to escape me when setting up systems.

But I did not pursue this any further. If you dont get accelerated video graphics with this older card, you dont get a decent DVD performance.
So, maybe they will someday fix this.
It is on a system that likely wont be used much.

What is your motherboard chipset? mine is an 82875 intel server motherboard.

---

### Post by flyingbrass on 2008-10-28
Fglrx works ok with my Radeon 9600.  I have desktop effects turned off.

To enable xv on these old 300 series cards you have to add the VideoOverlay option to xorg.conf. Here's mine:

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection 
```

Reboot or restart X for the change to take effect.

---

### Post by flyingbrass on 2008-10-28
> **perriccolo said:**
> How can i verify that i'm using fglrx driver?

Pull up a terminal and type fglrxinfo.  You should see something like this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.8087 Release

---

### Post by jtuchscherer on 2008-10-28
> **sdowney717 said:**
> well, I removed all entries from xorg.cong and was able to get 1024 by 768 with the free ati driver.
it will simply boot up without the 'no devices detected' or the low graphics message.
You dont know how much I hate seeing video problems and never seems to escape me when setting up systems.

But I did not pursue this any further. If you dont get accelerated video graphics with this older card, you dont get a decent DVD performance.
So, maybe they will someday fix this.
It is on a system that likely wont be used much.

What is your motherboard chipset? mine is an 82875 intel server motherboard.

Thanks for your reply. I got my problem with the radeon driver fixed by removing the fglrx driver. I didn't know that you need to physically remove the fglrx driver. Now with the radeon driver I get decent performance and can wait now until they have a fix for fglrx and the Radeon Mobility 9600.

---

### Post by biasquez on 2008-10-28
> **flyingbrass said:**
> Pull up a terminal and type fglrxinfo.  You should see something like this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.8087 Release

i have problem with my mobility 9600/9700 when i try to load fglrx module.
but have you fglrx installed from pkg xorg-driver-fglrx or downloaded from ati website?

---

