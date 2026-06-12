---
title: "ATI Radeon 9200 not working"
date: 2008-08-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by useResa on 2008-08-10
I have Xubuntu Intrepid installed on a PIII machine (result of hwinfo is attached for those who are interested).

I am trying to get 3D acceleration working in this installation.
For another installation on this box (Dreamlinux) I succeeded in this using the ati driver. However, when I try the ati driver in Xubuntu I get the error that no screens are detected. When I try the radeon driver, my screen switches into "sleep mode" and I can only restart by means of the Power button.

Next I read about the [xorg-driver-fglrx]("http://packages.ubuntu.com/intrepid/xorg-driver-fglrx") and I have tried to install it.
However, when I ran aticonfig the driver crashed (which I reported, see [bug #255846]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/255846"))

For reference, please find below the outcome of uname -a
```
Linux xubuntu-intrepid 2.6.26-5-generic #1 SMP Sun Aug 3 01:25:54 UTC 2008 i686 GNU/Linux
```and the outcome of lspci | grep -i vga
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
```I have read the thread [How do you install latest fglrx on Intrepid]("http://ubuntuforums.org/showthread.php?t=882210") but could not find an answer in that thread. Furthermore I never got the proprietary driver for this card properly working.

Does anyone have a suggestion on how I can get my card fully up and running?
BTW: Currently running Xubuntu with the vesa driver.

---

### Post by gjoellee on 2008-08-10
Read the posts here: [http://ubuntuforums.org/showthread.php?t=885564](http://ubuntuforums.org/showthread.php?t=885564)
that includes all drivers!

---

### Post by tepsipakki on 2008-08-10
fglrx does not support r200 based cards (including 9200) anymore.

---

### Post by useResa on 2008-08-10
> **gjoellee said:**
> Read the posts here: [http://ubuntuforums.org/showthread.php?t=885564](http://ubuntuforums.org/showthread.php?t=885564)
that includes all drivers!With this you mean that Intrepid is still and development and items may not work?? I am aware of this! I know that installation of Alpha and/or RC versions may result in a non working environment and/or may contain packages that (still) do not  work because they are under development.
IMHO I can still ask the question, can't I?
Maybe someone else has succeeded in getting it running and I could benefit from his/her knowledge. If not ... then at least I know.

> **tepsipakki said:**
> fglrx does not support r200 based cards (including 9200) anymore.  :confused:

From the page of [xorg-driver-fglrx]("http://packages.ubuntu.com/intrepid/xorg-driver-fglrx")
> Video driver for the ATI Radeon and FireGL graphics accelerators.

This version of the ATI driver officially supports:

 * RADEON X1300, X1600, X1800, X1900
 * **RADEON** 8500, 9000, 9100, **9200**, 9500, 9550, 9600, 9700, 9800
 * RADEON X800, X700, X600, X550, X300 series (AGP and PCI Express)
 * MOBILITY RADEON 9000, 9200, 9600, 9800, X700
 * MOBILITY RADEON 9000/9100 IGP Series
 * FireGL 8700, 8800, E1, E2, X1, X2, X3, Z1, T2
 * MOBILITY FireGL 9100, T2
 * RADEON XPRESS 200So AFAIK this package should support my card or am I misunderstanding something?

---

### Post by tepsipakki on 2008-08-10
right, the description should be updated and drop cards which it doesn't support anymore.

besides, no-one has a working fglrx in intrepid, since it doesn't support the new xserver..

---

### Post by InfinityCircuit on 2008-08-10
To solve the screen going into powersave mode you should be able to do this in /etc/X11/xorg.conf:

Under Video Device, set
Driver    "radeon"

Under Screen, set
DefaultDepth    16

---

### Post by useResa on 2008-08-11
> **tepsipakki said:**
> right, the description should be updated and drop cards which it doesn't support anymore.

besides, no-one has a working fglrx in intrepid, since it doesn't support the new xserver..Thanks for clearing this up.

> **InfinityCircuit said:**
> To solve the screen going into powersave mode you should be able to do this in /etc/X11/xorg.conf:

Under Video Device, set
Driver    "radeon"

Under Screen, set
DefaultDepth    16
I have tried this, but unfortunately it still entered sleep mode.
But thanks for the tip anyway.

---

### Post by UbuWu on 2008-08-12
You might be affected by this bug (I have a 9250): 
[https://bugs.edge.launchpad.net/xorg-server/+bug/133192](https://bugs.edge.launchpad.net/xorg-server/+bug/133192)

The solution is using the ati driver and putting the following in the Device section of xorg.conf:

Option "AGPMode" "4"

---

### Post by bpl07 on 2008-08-12
As the poster above said, fglrx doesn't work for intrepid yet, but you can get some pretty nice 2D and 3D effects with the open source drivers.  Make sure you completely remove fglrx (the fglrx radeon.ko file can conflict with the open source radeon.ko), then follow these [instructions for installing the driver and drm]("http://www.phoronix.com/forums/showthread.php?t=9951").  You can ignore the part about upgrading xserver and xorg, it was written for hardy but works perfect in intrepid.  Also, if you search around, there are tons of optional settings to improve the quality through xorg.conf.

---

### Post by RAOF on 2008-08-13
You could do the above, but since your card is hardly cutting-edge you might as well just go with the drivers in the official repositories.  Adding the 3rd party repositories from above won't buy you anything interesting.

---

### Post by useResa on 2008-08-24
> **UbuWu said:**
> The solution is using the ati driver and putting the following in the Device section of xorg.conf:

Option "AGPMode" "4"This indeed does prevent the "sleep mode", but after that the desktop starts in "Low graphics mode"

---

### Post by je1117 on 2008-08-24
in the /etc/X11/xorg.conf file, under the "Device" section add the line Option BusType "PCI" . I have a radeon 9200 that did the same thing, and I have never got the closed source drivers to work. Also, playing with the AGP speed never changed anything either. ALWAYS have had to put that line in xorg. Make sure you boot in recovery mode!

---

### Post by scradock on 2008-08-24
> **tepsipakki said:**
> right, the description should be updated and drop cards which it doesn't support anymore.

besides, no-one has a working fglrx in intrepid, since it doesn't support the new xserver..

This is rather alarming. You are saying that the open-source drivers will be dropping/have dropped support for some older cards? Can you point us to a current list of supported cards, please? Will there continue to be a version available for those of us with legacy cards, or are we on our own?

This is especially poignant while the proprietary drivers are not working with the new Xorg version, but it will always affect people who prefer not to use proprietary drivers and believed that Ubuntu would provide open source alternatives......

---

### Post by The Keeper on 2008-08-25
You've misunderstood. FGLRX is the ATI's own proprietary driver and it has dropped support for older cards long time ago. The open-source drivers have not dropped support for any of the Radeons.

I believe the FGLRX driver does not support R100 and R200 series of Radeons, R300 and newer are still supported.

---

### Post by useResa on 2008-08-25
> **The Keeper said:**
> You've misunderstood. FGLRX is the ATI's own proprietary driver and it has dropped support for older cards long time ago. The open-source drivers have not dropped support for any of the Radeons.I understood exactly the same as scradock has written.

Since [the post of tepsipakki]("http://ubuntuforums.org/showpost.php?p=5562444&postcount=5") is a reply to my quote from the [xorg-driver-fglrx page]("http://packages.ubuntu.com/intrepid/xorg-driver-fglrx") on which is stated
> This version of the ATI driver officially supports:
 * RADEON X1300, X1600, X1800, X1900
 * RADEON 8500, 9000, 9100, 9200, 9500, 9550, 9600, 9700, 9800
 * RADEON X800, X700, X600, X550, X300 series (AGP and PCI Express)
 * MOBILITY RADEON 9000, 9200, 9600, 9800, X700
 * MOBILITY RADEON 9000/9100 IGP Series
 * FireGL 8700, 8800, E1, E2, X1, X2, X3, Z1, T2
 * MOBILITY FireGL 9100, T2
 * RADEON XPRESS 200

tepsipakki stated that this was wrong and that the description should be updated.

So AFAIK I was not revering to a proprietary driver but to an Ubuntu package.

---

### Post by useResa on 2008-08-25
> **je1117 said:**
> in the /etc/X11/xorg.conf file, under the "Device" section add the line Option BusType "PCI" . I have a radeon 9200 that did the same thing, and I have never got the closed source drivers to work. Also, playing with the AGP speed never changed anything either. ALWAYS have had to put that line in xorg. Make sure you boot in recovery mode!Thank you!!
This indeed solved the issue ... ati driver is now working again!

---

### Post by scradock on 2008-08-25
> **useResa said:**
> I understood exactly the same as scradock has written.

Since [the post of tepsipakki]("http://ubuntuforums.org/showpost.php?p=5562444&postcount=5") is a reply to my quote from the [xorg-driver-fglrx page]("http://packages.ubuntu.com/intrepid/xorg-driver-fglrx") on which is stated


tepsipakki stated that this was wrong and that the description should be updated.

So AFAIK I was not revering to a proprietary driver but to an Ubuntu package.

Yes, but The Keeper is right - that refers to the Ubuntu package containing the proprietary fglrx driver! I was probably confused, but would still like to know which cards are no longer supported by xorg-driver-fglrx, as well as confirmation that the open-source drivers (ati, radeon) continue to support all the ATI cards listed.......

---

### Post by useResa on 2008-08-26
> **scradock said:**
> Yes, but The Keeper is right - that refers to the Ubuntu package containing the proprietary fglrx driver!Thanks for clarifying this. 

> **scradock said:**
> I was probably confused, but would still like to know which cards are no longer supported by xorg-driver-fglrx, as well as confirmation that the open-source drivers (ati, radeon) continue to support all the ATI cards listed.......
+1

Finally a screenshot to proof all eye candy is working ;)

---

### Post by RedBird on 2008-09-09
Can you post the output of the Direct Rendering result here?
```
glxinfo | grep direct
```

---

### Post by ibizatunes on 2008-09-09
I have a friends computer with 8.04 install with this graphic card installed, i have compiz enable but due to the open source drivers not having DRI2 (i think), when he fast user switches, it loses the AWN dock, will 8.10 open source drivers fix this? Or can I get proprietary drivers now (in 8.04 I couldn’t get them), in restricted hardware to resolve this in the next release?
I cant test 8.10 on his machine, so some information would be MOST helpful!!

---

### Post by RAOF on 2008-09-09
> **RedBird said:**
> Can you post the output of the Direct Rendering result here?
```
glxinfo | grep direct
```

It's worth mentioning that this is useless with Mesa 7.1 - the software renderer now *also* supports direct rendering, so
```

direct rendering: yes

```
is no longer any guarantee that your drivers are working.

---

### Post by Peaceable Frood on 2008-09-09
Eh, since the ati driver now supports 3D for my card (x1400), I'm never ever going back to fglrx again. No more hassles of trying to compile the modules, or odd bugs like not supporting 1680x1050 (happened in one "stable release") My computer sleeps/hibernates without a hitch too.

---

### Post by useResa on 2008-09-10
> **Peaceable Frood said:**
> Eh, since the ati driver now supports 3D for my card (x1400), I'm never ever going back to fglrx again.Please note that I only tried the fglrx driver since initially I could not get the "eye candy" working with the ati driver and since I thought the fglrx driver also supported my card.
The topic of this thread was also not so much if fglrx would work with my card, but to get my card working anyway.
 
Now that I have my card running perfectly with the ati driver I am not going for the fglrx driver. Why bother ;)

---

### Post by inportb on 2008-09-10
... because fglrx supports OpenGL 2.1 ;p (which you might want if you want to make better use of your hardware). But the opensource radeon driver's been working just fine for me so far, and I don't have to use the extra features just yet =p

---

