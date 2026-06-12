---
title: "Trying to load 10.04, but menu is unresponsive."
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by adamadamadam on 2010-05-23
I've burnt the iso image onto a disk and reset my computer (running XP atm). Once i get to the main menu (after the language menu) the only option that is responsive is the "boot from disk" option. The 'run without installing', 'install', 'check memory' and 'check disk options' don't do anything. When i select them the disk does spin faster in the drive for a few seconds, but nothing happens. 
I've burnt two discs, one with ISORecorder and one with Infrarecorder and they both have the same problem.
Have i done something wrong?

---

### Post by cclloyd9785 on 2010-05-23
i have this exact same problem.  tried on 2 CD-R with IMGBurn

---

### Post by adamadamadam on 2010-05-23
now on offer, twice the glory for whoever can solve our problem :P

---

### Post by cclloyd9785 on 2010-05-23
and the even stranger thing is when i downloaded it the first time, a completely different screen showed up, not the one that i have now.

---

### Post by wojox on 2010-05-23
When you get to the options menu press F6 and select **nomodeset**

See if that does anything.

---

### Post by rowemi on 2010-05-23
I'm experiencing the same behavior on a Dell Inspiron E1505.  I rest the Setup to boot from CD first, UBUNTU startup happens, I select English, and get the "Try Ubuntu..", "Install U..", "Check disc...", "Test Memory", and the "Boot from first hard drive".   If I hit the ESC key, I get a popup asking if I want leave the graphical boot menu and start the text mode interface.
 
The only one that works in "Boot from first hard drive", which takes me to XP.
 
I built the ISO image on 29-April-2010, but tonight was the first opportunity to try it.
 
Any help would be greatly appreciated.
Cheers

---

### Post by rowemi on 2010-05-23
I tried nomodeset.  There is a check in fornt of this option -- what do I do to make it do something with this option?

---

### Post by wojox on 2010-05-23
> **rowemi said:**
> I tried nomodeset.  There is a check in fornt of this option -- what do I do to make it do something with this option?

After it's selected then click on Try Ubuntu...

---

### Post by adamadamadam on 2010-05-23
Sorry, but nothing new. Same problem persists

---

### Post by rowemi on 2010-05-23
I just sits there with nothing happening :-(

---

### Post by rowemi on 2010-05-23
> **rowemi said:**
> I just sits there with nothing happening :-(
 
Add a 't' after the 'I'.  Fingers don't move as fast as they use to.

---

### Post by wojox on 2010-05-23
Do you all know what graphic card/chip your using?

---

### Post by rowemi on 2010-05-23
> **wojox said:**
> Do you all know what graphic card/chip your using?
I'm running a ATI MOBILITY Radeon X1300
BIOS 009.012.001.009.200.055
64 MB memry
Native Res 1200 by 800

---

### Post by cclloyd9785 on 2010-05-23
I just tried booting again, but before i hit F6, i hit enter on the install ubuntu, and it worked :\  Idk what happened but i also heard a loud beep.

---

### Post by adamadamadam on 2010-05-23
I have no idea,
is control panel->system->device manager the place to find out?

---

### Post by rowemi on 2010-05-23
> **adamadamadam said:**
> I have no idea,
is control panel->system->device manager the place to find out?
 
On powerup go to setup  (on my Dell it is F2)  It will have options for setting boot device order and you can see most of your hardware and firrware models/versions/etc.

---

### Post by wojox on 2010-05-23
> **adamadamadam said:**
> I have no idea,
is control panel->system->device manager the place to find out?

1. In Vista, click the Start button, type dxdiag in the search bar, and press Enter.

In XP, from the Start button, select Run... . Type dxdiag and click OK.

2. The DXDIAG panel will open. Click the Display tab.

Your video card's name and chipset will be identified in this panel. When you're finished, click Exit to close the panel.

---

### Post by adamadamadam on 2010-05-23
Geforce Go 6200
128MB
1280 x 768
This help?

---

### Post by wojox on 2010-05-23
> **rowemi said:**
> I'm running a ATI MOBILITY Radeon X1300
BIOS 009.012.001.009.200.055
64 MB memry
Native Res 1200 by 800

Try and put the cd in and wait for the boot menu
hit the escape key to get to the command line
type:

```
live-install xforcevesa
```

Sorry I don't have experience with ATI.

Have you tried Ubuntu 9.10

---

### Post by wojox on 2010-05-23
> **adamadamadam said:**
> Geforce Go 6200
128MB
1280 x 768
This help?

You have nvidia like me. That setting **nomodeset** was the only way I could get it to work. You pressed F6 and then selected it with the space bar and tried to load it?

---

### Post by adamadamadam on 2010-05-23
Yep, 5th time and still not working. Im using a Sony Vaio. Would that be a factor?

---

### Post by wojox on 2010-05-23
> **adamadamadam said:**
> Yep, 5th time and still not working. Im using a Sony Vaio. Would that be a factor?

I'm not sure of that. Have you tried a different version like Karmic 9.10 [http://releases.ubuntu.com/9.10/](http://releases.ubuntu.com/9.10/)

---

### Post by adamadamadam on 2010-05-23
> **wojox said:**
> I'm not sure of that. Have you tried a different version like Karmic 9.10 [http://releases.ubuntu.com/9.10/](http://releases.ubuntu.com/9.10/)
Downloading it now, will let you know how it goes. Cheers

---

### Post by wojox on 2010-05-23
> **adamadamadam said:**
> Downloading it now, will let you know how it goes. Cheers

You may be able to install that and then upgrade from it.

---

### Post by wojox on 2010-05-24
You could also try during boot, on the purplish screen, press esc. Then it will pull up a menu press "f6" for other options and try installing with "nomodeset"

---

### Post by adamadamadam on 2010-05-24
9.10 worked wonderfully, not a single problem. Im wanting to uninstall windows, is it best to install Ubuntu first, and then unintall windows, or do windows first?

---

### Post by wojox on 2010-05-24
Just put the cd in and install it. When you get to the Format section tell it to use the whole disk. I will overwrite Windows and install Ubuntu

---

### Post by adamadamadam on 2010-05-24
wonderful, thanks a lot for your help wojox. Will attempt to upgrade as soon as it's done installing. At least I have 9.10 if 10.04 doesn't work.

---

### Post by adamadamadam on 2010-05-25
10.04 is all up and working, through the upgrade from 9.10 Thanks again

---

