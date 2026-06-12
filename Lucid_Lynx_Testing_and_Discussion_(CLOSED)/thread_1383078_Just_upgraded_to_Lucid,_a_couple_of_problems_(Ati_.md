---
title: "Just upgraded to Lucid, a couple of problems (Ati Card)"
date: 2010-01-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by AllRadioisDead on 2010-01-16
Hi everyone,
I've just recently upgraded to lucid and I'm very impressed, especially for such an early alpha. After the upgrade, I have 2 problems though.
The first is the ati open source drivers I was using in Karmic. I had the xorg edgers repo enabled, however during the upgrade all my third party ppa's were disabled. Upon re-enabling them, I still have no desktop effects.
The second is with plymouth, on boot plymouth tries to start but fails, saying it couldn't connect to the plymouth server or something of that sort.

The thing that amazes me most though is the boot speed, I hated booting up Karmic, it was never a smooth experience for me with the 2 splash screens. Hopefully I can get Plymouth up and running and it can be nice and smooth.

---

### Post by jerrylamos on 2010-01-16
Probably should be posted on the Lucid forum, see:

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

There are some bugs see the release note for Alpha 2

[http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)

Good luck.  Updates can kill....

Jerry

---

### Post by AllRadioisDead on 2010-01-16
Hmm, thanks.
I read around through the lucid forums and I'm not the only one with the plymouth problem, but I haven't found a fix yet.
As I couldn't find anything on the ati driver either, the only thing mentioned in the lucid bugs is:

[LIST]
[*] The fglrx binary driver for ATI video chipsets does not yet support the X server in Lucid. As a workaround, users should use the open source -ati  driver instead. ([506656]("https://bugs.launchpad.net/bugs/506656")) 

This however is of no significance because I'm already trying to use it.
[/LIST]

---

### Post by AllRadioisDead on 2010-01-17
Bump!

---

### Post by clhsharky on 2010-01-17
HI

What chip do you have?
A fresh instal Lucid-a2 with ATI-X1650 and 3D out of the box here.


Sharky

---

### Post by AllRadioisDead on 2010-01-18
I'm running a Radeon HD 4850.

---

### Post by Nickedynick on 2010-01-18
I've got a 4830, tried upgrading too and it screwed up. Try doing a fresh install - mine worked flawlessly straight from the disc without even having to enable restricted drivers. As far as I know the upgrade path isn't complete for Karmic to Lucid yet, hence the issues.

---

### Post by AllRadioisDead on 2010-01-18
> **Nickedynick said:**
> I've got a 4830, tried upgrading too and it screwed up. Try doing a fresh install - mine worked flawlessly straight from the disc without even having to enable restricted drivers. As far as I know the upgrade path isn't complete for Karmic to Lucid yet, hence the issues.
Enabling restricted drivers would download the proprietary driver, but there is none available for lucid anyways. I do not want the proprietary drivers, I'd like to use the open source ones.

---

### Post by Sophont on 2010-01-19
I recently tried Lucid on my laptop with ATI 4670 and it worked fine - incl. full effects - out of the box.

I recommend downloading the live CD iso of Alpha 2 and see if that works right away.
If it does - then it's just a problem with the upgrade path.

---

### Post by ranch hand on 2010-01-19
I am not a fan of desktop effects but I have the Xorg-Edgers ppa on one of my 10.04 installs runs great and they are very much ahead of the curve.

My card (see sig) is doing great on that install with the effects set at extra.  This tends to freeze the box tight with out their stuff.

---

### Post by emarkay on 2010-01-19
I wouldn't do an upgrade on an Alpha, IMHO, but my ATI card ([COLOR=Purple]ATI HD2600-512 RAM) [/COLOR]is working fine, albeit with no Restricted Driver activated.   

BTW, What is the process for manually loading the Open Source -ati driver so I can test that.

Thanks.

---

### Post by goodrench on 2010-02-19
I have a Radeon 4670 and 3D works great out of the box (Lucid), but I can't get the fan to settle down.
Is there a way to control this without the proprietary driver?
Installed on a home theater pc. Now way we can watch tv with the fan that loud.
Maybe it is time to buy a fanless one or a new ION ITX board to build a new htpc.

---

### Post by nikopol on 2010-03-11
Ditto here - this problem has been there for the last 7 days or updates with me. A bit annoying noise wise - well will check if I can get it to settle someway.

---

### Post by zika on 2010-03-11
Did You try with> Option          "ClockGating"           "on"
        Option          "DynamicPM"             "on"
        Option          "ForceLowPowerMode"     "on"
in /etc/X11/xorg.conf...?
(If You're using open-source radeon driver...)
> ~$ cat /etc/X11/xorg.conf
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "radeon"
        Option          "ClockGating"           "on"
        Option          "DynamicPM"             "on"
        Option          "ForceLowPowerMode"     "on"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by nikopol on 2010-03-11
> **zika said:**
> Did You try within /etc/X11/xorg.conf...?
(If You're using open-source radeon driver...)

Thanks for the tip - sadly no joy with that either.

---

### Post by icek on 2010-03-11
this thread may help [http://www.phoronix.com/forums/showthread.php?p=116577&posted=1#post116577](http://www.phoronix.com/forums/showthread.php?p=116577&posted=1#post116577) , I hope catalyst 10.3 will be lucid ready :-)

---

