---
title: "Blank screen when attempting to install Lucid Lynx"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by fuwkej on 2010-05-01
Disc: 64-bit Ubuntu 10.04 desktop installation CD.

I used the disc to install Ubuntu on another computer and it worked fine, so the issue seems to arise when trying to install Lucid Lynx on my main computer.

Sequence:

1. Boot CD drive, Ubuntu loading screen appears with 5 blinking red dots
2. Red dots all light up and then monitor blanks out
3. CD is spinning still, and activity lights are blinking but the monitor does not work at all
4. Tried again with VGA cord instead of DVI cord, still blank

My video card is ATI Radeon HD 5700 Series. I'll have to stick with Karmic Koala until I can resolve this issue.

---

### Post by fuwkej on 2010-05-01
anyone?

---

### Post by Leischa on 2010-05-01
Same problem. No solution. Sorry.

---

### Post by romulus on 2010-05-01
I have the same problem (live CD) with my Nvidia GeForce 7050 PV / nForce 630a integrated graphics. NO video and monitor goes to sleep. but I can hear the Ubuntu startup sound through my speakers. WHY!!!!!!!!!!:confused:

However it works fine on the already installed 9.10 upgraded to 10.04 with one exception...when I boot from a "turned off" PC the graphics revert back to basic with an error message about the Nvidia driver and once I'm in 'X' I can reset driver and everything works fine.

If I start in Windows then _reboot_ and start Ubuntu = no problems.

I guess this version depends on Windows!:lolflag:

---

### Post by romulus on 2010-05-01
I found this thread to be very useful. I can now use my live CD by pressing F6 and checking nomodeset from menu. see link below

[http://ubuntuforums.org/showthread.php?p=9195971#post9195971](http://ubuntuforums.org/showthread.php?p=9195971#post9195971)

---

### Post by romulus on 2010-05-01
I just did a fresh install using nucleuskore's instructions (see previous post).

Everything is working great! No more nvidia error messages at startup!

I hope someone else finds this useful.

---

### Post by fuwkej on 2010-05-01
still trying to fix this. I tried every suggestion in [http://newyork.ubuntuforums.org/showthread.php?p=9200710](http://newyork.ubuntuforums.org/showthread.php?p=9200710), and another thread. None of the solutions worked for me.

Tried replacing quiet splash with nomodeset for boot command, didn't help.
Added i915.modeset=1 to boot command, didn't change anything.

Considering I have a VERY common ATI graphics card, you'd think the guys over at Ubuntu would have caught this.

I have had 'some' success. I burned an alternate CD (64-bit) and installed Ubuntu manually. It seemed to have installed fine, but it still does not boot at all. Trying varying options in the grub2 boot options right now.

---

### Post by BobDoLe on 2010-05-02
> **laverabe said:**
> Disc: 64-bit Ubuntu 10.04 desktop installation CD.

I used the disc to install Ubuntu on another computer and it worked fine, so the issue seems to arise when trying to install Lucid Lynx on my main computer.

Sequence:

1. Boot CD drive, Ubuntu loading screen appears with 5 blinking red dots
2. Red dots all light up and then monitor blanks out
3. CD is spinning still, and activity lights are blinking but the monitor does not work at all
4. Tried again with VGA cord instead of DVI cord, still blank

My video card is ATI Radeon HD 5700 Series. I'll have to stick with Karmic Koala until I can resolve this issue.

i have the same problem ... and i also am doing a 64bit install with an ATI Radeon HD 5000 series card (2 5670 cards in crossfire). 
tried the F6-nomodeset thing (mentioned in link above) and no luck... then i just added ```
i915.modeset=0 xforcevesa 
``` to the boot parameters on the install option per something stated somewhere in the above link and finally got the install going. 

i can tell this is going to be some nightmare :popcorn:

---

### Post by BobDoLe on 2010-05-02
update for me.. after my boot option, it installed fine and i was able to run the new catalyst 10.4 driver (downloaded from vendor and simply executed it). everything...works...fine??..! :confused::P

---

### Post by fuwkej on 2010-05-02
**Solution** (that worked for me)

1. Use alternate install disc for installation (takes a bit longer)
2. Reboot and hold shift during startup, select recovery boot option (second option)
3. System should boot up in low graphics mode. Install hardware drivers from ATI under System>Administration>Hardware Drivers
4. Reboot, and everything works great

---

### Post by jazz53 on 2010-06-02
OK that worked for an install, how about a fix for running from a live cd?
I can not load from Live CD
have a ati radeon 5700.
Tried both 32 & 64, same screen blanks and continues to load. Must be a video driver problem.

Help Please

---

