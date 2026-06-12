---
title: "Halfway through install from CD, Ubuntu returns error message about CD drive being bu"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by ChipMicro on 2008-11-25
This is an odd one.  I have a bona fide install CD (not downloaded and burnt - this was handed out at a trade show) and am trying to install it on an older PC (Compaq) that was running Windows 98.  I tried the outright install and it failed with a mysterious black screen of non-action, so then I tried the mode where you insert the CD and can install it so that you can run it after booting up in Windows.

It gets about 2/3 (a guess) of the way through the installation when it comes up and returns the message that the CD drive is busy, so it can't go on with the install.  There is one CD drive on the box, and the reason it's busy is because Ubuntu itself is using it, but somehow it isn't cognizant of the fact.  I can't use Wubi b/c this PC doesn't have a modem, and the preferred method of installing it from the CD so that it replaces Windows won't work.

I'm not new to OS's (I'm a mainframer, mostly), but have to admit I'm a little green with the particulars of installing Ubuntu, so hopefully this is something someone else has seen and can shoot me a little info on.

Thanks!  CM

---

### Post by gn2 on 2008-11-25
Is the CD that you have a conventional Live CD?
You need a minimum of 384mb of RAM to install from this CD.

Difficulties with installing can usually be cured by using the Alternate CD which is install only.
You can download it as an .iso and burn it to CD (or DVD) as an image.

Another option is to use the Live CD, press F6 at boot and type the additional boot parameter: only-ubiquity

---

