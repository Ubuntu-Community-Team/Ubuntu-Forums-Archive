---
title: "ATI Catalyst Driver"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jaoc223 on 2010-03-25
I'm using an iMac 24" with Radeon HD 2400 XT can I use the new ati catalyst driver?

---

### Post by iRiUX on 2010-03-25
> **jaoc223 said:**
> I'm using an iMac 24" with Radeon HD 2400 XT can I use the new ati catalyst driver?

Try and see: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.3&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.3&lang=English)

---

### Post by TrueJournals on 2010-03-25
iRiUX: That's actually NOT the latest catalyst driver.  The version currently in the Lucid repositories is a pre-release of the 10.4 version.  The version you linked doesn't work with the version of Xserver included in Lucid.

jaoc223: Open "Hardware Drivers" under System>Administration, and see if it lists ATI Fire GL (it should, your card appears to be supported).  Select that item, and click enable.  Reboot and you should be using the latest driver.  If not, you'll have to open a terminal and do a ```
sudo aticonfig --initial -f
``` then reboot again.  You can always check if you're running the ATI driver by running fglrxinfo.  Your output should be something like this: ```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3650
OpenGL version string: 3.2.9737 Compatibility Profile Context
```  If it just gives an error, you are NOT using the proprietary ATI driver.

---

### Post by godhika on 2010-03-25
Jockey does not show the Catalyst drivers at the moment. Should come within the next weeks

---

### Post by TrueJournals on 2010-03-25
Are you sure?  Even though I installed the driver manually, Jockey is showing "ATI Fire GL".

If Jockey isn't showing the packages, running this in a terminal should install everything you need:
```
sudo apt-get install fglrx fglrx-amdcccle fglrx-modaliases
```

---

### Post by iRiUX on 2010-03-26
I have the open source drivers install on my laptop because catalyst 10.4 wouldn't work. I'm really amazed at the performance of this thing on my card: ATI 4570. If Catalyst doesn't work for you either, you can install the open source drivers with the following command:

**sudo apt-get install xserver-xorg-video-ati**

Everything is so snappy, Im not used to that with Catalyst. However, I haven't tried catalyst on my 10.04 Kubuntu yet, so it could be due to other things too that its so snappy. Composition fully enabled, GLXGEARS:
3519 frames in 5.0 seconds = 704 FPS
3687 frames in 5.0 seconds = 737 FPS

glxinfo:
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV710 9553) 20090101  TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1-DEVEL

---

### Post by NightSky256 on 2010-04-02
> **iRiUX said:**
> I have the open source drivers install on my laptop because catalyst 10.4 wouldn't work. I'm really amazed at the performance of this thing on my card: ATI 4570. 

And what about the fan and the Ati card throttling down ?

On my HP-DV6 with the same (great ;)) Ati card, open source drivers keep the card at the highest speed, even with compiz effects disabled, and 10.4 seems to not work... with 10.3 on Karmic i can get a very high performance from this card, some games runs better on wine under Karmic than on Window$ 7...

and, while i'm simply watching a movie on a flash based website, on karmic the pc is keep fresh... on lucid i can put corns on it to make them pop :popcorn:

btw i'm sure that Ubuntu guys and Amd guys are making a very good (even if hard) job on ati drivers... and 10.4 will be ok for the release day...

---

