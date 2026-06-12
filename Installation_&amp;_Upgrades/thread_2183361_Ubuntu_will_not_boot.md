---
title: "Ubuntu will not boot"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by Douglas_Fuller on 2013-10-24
Machine:

Asus Maximus IV Extreme-Z
Intel core i7-2600K running at 4.6 (Water cooled)
Ram 24gb 1600
1 SSD with Win 7/64
6 HDD various sizes
1 DVD burner
Video HIS HD6870


Problem:  I downloaded the iso file and burned a dvd with ubuntu 12.04. I then installed ubuntu, as a stand alone OS, onto a clean 80gb HDD. (I did this twice in case of a faulty install) I then went into the BIOS and selected that HDD to boot. The computer then boots to a black screen with a blinking cursor in the upper left corner and then will not do anything else. It does boot into windows normally.

I would like to be able to install and learn how to use Ubuntu. Please help.

---

### Post by Bashing-om on 2013-10-24
Douglas_Fuller; Hi ! Welcome to the forum. 

What we often see in this situation of a "black screen" is no graphics driver is installed.
Often a boot parameter of "nomodeset" will permit booting the system (degraded graphics) and at a later time installing the appropriate driver:
Try:
Boot the liveCD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; and choose "nomodeset".
Enter key to continue the boot process to the GUI desk top;

If this is successful in the liveDVD, will see what can be done on the install.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Douglas_Fuller on 2013-10-24
Hi Bashing-om,

I did try what you suggested, but booting from the DVD has not been a problem. I did boot the DVD as you prescribed and the boot, although a little different ended up as a successful boot. When I again tried a boot from the HDD that had ubuntu installed on it, it again booted directly into the black screen with the blinking cursor in the upper left corner (perhaps a couple of lines from the top). it did not even get to the purple splash screen. Am I supposed to be getting a display driver from the DVD that somehow intalls itself onto the HDD version? It seems that the install on the HDD is not receiving the signal to boot. My apologies if I am not understanding ubuntu and Linux as I am older and was brought up on DOS and various versions of Windows.

---

### Post by Bashing-om on 2013-10-24
Douglas_Fuller; Hey;

The graphics drivers available on the liveDVD as not the same as what will be in the install.

Your "Video HIS HD6870" I am not familiar with.. but as you have no problem booting the liveDVD.
Try this in the install:

Boot up the real install of ubuntu:
As soon as the bios screen clears, depress and hold the left shift key -> grub menu,
With the top entry in this list highlighted (default) press the "e" key for edit mode -> boot parameters screen,
In the boot parameter screen, arrow down and across to the term "quiet splash" and insert that term "nomodeset - without the quotes,
key combo ctl+x to continue the boot process to the GUI login.
Login here;
Do you now boot to the desk top ? .. degraded graphics at this point is OK .. will fix that directly. If you now boot to the desk top.

[INDENT][INDENT]this is doable
[/INDENT][/INDENT]

---

