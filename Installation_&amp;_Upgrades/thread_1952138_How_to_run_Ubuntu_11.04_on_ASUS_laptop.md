---
title: "How to run Ubuntu 11.04 on ASUS laptop?"
date: 2012-04-03
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2012-04-03
I have the install CD but can't get it to run or boot off the Install CD for 11.04 on an ASUS laptop Model X54C. Tried getting it to boot off the CD by hitting a couple F keys, that worked for Toshiba laptop and a couple Dell desktops but ASUS won't respond to this.
What do you have to do to give it a test run, then install off that CD?

My install CD installed 11.04 fine on my Toshiba laptop and two Dell desktops. Just can't figure out how to get it to work for this ASUS laptop.

What's the trick?

---

### Post by QIII on 2012-04-03
How does your documentation say to get to your BIOS setup?

You will have to set your boot order to boot from the optical drive first.

---

### Post by wojox on 2012-04-03
My asus eeepc is F2. May work.

---

### Post by cybrsaylr on 2012-04-03
F2 gives me BIOS info with the:

Main/advanced/boot/security/save & exit

But the 'boot' section seems more complicated than my other PCs.
There is no simple choice to boot from CD/DVD drive with this ASUS.

---

### Post by cybrsaylr on 2012-04-03
Hit F2 and was trying some of the other boot options but it seems no matter which one is selected Win7 boots up and totally ignores Ubuntu.

---

### Post by Mark Phelps on 2012-04-04
> **cybrsaylr said:**
> ... But the 'boot' section seems more complicated than my other PCs.
There is no simple choice to boot from CD/DVD drive with this ASUS.

According to their manual, YES there is such an option.

You select Boot Option #1 on the screen and then select which of the two devices to be the first in the boot sequence.  The CD/DVD drive is shown as "Optiarc DVD RW AD-7585H"

---

### Post by cybrsaylr on 2012-04-04
Decided to go to the ASUS Forums and ask.

Got the solution fairly quick:
> If you want to boot from a cd, instead of hitting F2, hit ESC. F2 gets you into the bios where you can set the boot device priorities. ESC will just pop a menu allowing to choose boot from HDD, ODD and if available/enabled network or USB.

Did that and it worked fine.
Am in the process of installing 11.04 on that ASUS notebook right now.

Some reviews I checked claim ASUS plays very well with Ubuntu.

---

