---
title: "graphics not working with live CD - 12.04 nVidia GeForce 8300 GS"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by JoeGregory on 2013-11-03
Hi,

I currently have a Dell Inspiron 531 (AMD 64 bit). I have an Ubuntu partition which I messed up during an upgrade some years ago and gave up on Linux. 
The kids now simply run the MS Vista partition from the Grub loader. 

Decided to come back to it now, downloaded the 12.04 LTS iso file, burnt a DVD and tried to run Ubuntu (live CD) before installing. Graphics are messed up and I can't see any of the controls to exit etc. 

Graphics card worked perfectly with previous versions of Ubuntu - can this be the problem now?

JG

---

### Post by Bashing-om on 2013-11-03
JoeGregory; Hi !

I expect that graphics card to have good support.
For fault isolation establish a solid foundation:
a) verify that the downloaded .iso integrity;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
b) insure there is a good burn:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
c) Check the install disk disk:
DVD drive is set as 1st boot priority in bios.
Boot the liveDVD, as soon as the bios screen clears depress and hold the left shift key -> language screen, escape key to accept the defaults -> boot options screen -> "check disk".

All good to this point ? Now try and boot ubuntu, isolating to a graphics problem .
At this boot options screen, press the f6 key and 
arrow down to the preset option(s)- choose "nomodeset" - space or enter to accept and then the escape key to exit;
Enter key to continue the boot process to the GUI desk top; At this point degraded graphics is acceptable;
Does the Desk top load ? 

Launcher on the left of the screen -> System Settings -> Addition Drivers;
Install the recommended drivers.

If there is now good graphics and a stable desk top, we know what to do in the actual install. Further advise pending these results.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

