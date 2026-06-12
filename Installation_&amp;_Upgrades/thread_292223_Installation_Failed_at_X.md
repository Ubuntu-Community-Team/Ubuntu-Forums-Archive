---
title: "Installation Failed at X"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by mumebuhi on 2006-11-03
I have a Dell 2007FPb monitor and Dimension 9150. The Ubuntu installations (both 6.06 and 6.10) failed at the X configuration. It gave me a blue screen with messages:

(WW) ATI: PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI: PCI Mach64 in slot 1:0:1 could not be detected!
(EE) No devices detected.
Fatal server error:
no screens found

Thank you.


Buhi

---

### Post by wpshooter on 2006-11-03
Have you tried installing with safe video mode option ?

---

### Post by mumebuhi on 2006-11-03
I just tried it (safe mode installation) but it failed with the same diagnosis.


Buhi

---

### Post by wpshooter on 2006-11-03
1) Did you check the integrity of your CDs by running the verification test found on the Ubuntu initial boot screen menu.

2) If they passed verification, then try the **ALTERNATE** CD, instead of the **DESKTOP** CD.

---

### Post by mumebuhi on 2006-11-03
Yes, they passed the verification.

From the description of Alternate Install CD, I don't see anything in Alternate Install CD that will help configuring X. Does it have a better support for X? I am a newbie to Ubuntu so pardon me.

---

### Post by tedwick on 2006-11-03
same exact thing going on. dell dimension e510 with an ATI x600. Dell 2007wfp. doesn't work with regular or safe graphics install. iso matched the checksum, it verified itself after boot as well.

what i want to know is why 6.10 doesn't work, but 6.06 safe worked, and if there's a workaround... i'd really like to know if 6.10 actually works with my system, and having gparted is really helpful on install... so the alternate text install is, while not out of the question, much less preferable.

---

### Post by rionoco on 2006-11-03
i think your problem is with th ATI graphic card.
try this:

sudo apt-get install xserver-xorg-video-ati
if this doesn´t work.. cause it didn´t find any candidate..
try this:

cat/proc/version (to find your kernel)

then:

sudo apt-get install linux-headers-version-(and the number of your kernel)

maybe it works for you :D

---

### Post by mumebuhi on 2006-11-03
OK, the installation worked with 6.06.1 LTS 64-bit in safe graphics mode.

Now, in /etc/X11/xorg.conf file at "Screen" section, "1600x1200" actually is listed as one of the modes. However, the option is not available when I try to change the screen resolution via System | Preferences | Screen Resolution.

Do I need to install another ATI driver? I have no experience with video driver installation/upgrade. Can anybody help me on this?

Thank you.


Buhi

---

