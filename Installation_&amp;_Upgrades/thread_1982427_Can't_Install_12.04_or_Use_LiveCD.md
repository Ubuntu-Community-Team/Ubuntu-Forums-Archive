---
title: "Can't Install 12.04 or Use LiveCD"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by callen41 on 2012-05-18
I'm trying to install Ubuntu but I keep receiving a B43 Firmware error.  When I try to boot into the live CD the screen goes black and nothing ever happens.

I have "nomodeset" on.  Without it I can't even get to the screen that displays the error.  Trying to install just leads me to a black screen.

---

### Post by darkod on 2012-05-18
Except nomodeset also add the parameter to blacklist b43, I think it was like:
blacklist.b43=1

You might need to install or activate a different b43 driver once it loads.

---

### Post by callen41 on 2012-05-18
> **darkod said:**
> Except nomodeset also add the parameter to blacklist b43, I think it was like:
blacklist.b43=1

You might need to install or activate a different b43 driver once it loads.

How?  I can't type anything.

---

### Post by darkod on 2012-05-18
If you are activating the older type menu about nomodeset, you should be able to add another parameter too. I think if you press any key when Try Ubuntu is selected from the menu, it will show the boot line where you can add parameters.

---

### Post by callen41 on 2012-05-18
Okay so where should I type "blacklist.b43=1".

The line looks something like this: "a=b x=y --".

Should I add it in at the start or end of the line?  Or just anywhere before the --?

---

### Post by darkod on 2012-05-18
At the end before the -- is enough. Should be. :)

---

### Post by callen41 on 2012-05-18
Sorry to bombard you with questions but it said something like mmio is already in use.  It disappeared before I had the chance to right it down exactly.

Also, I'm still getting the error: "b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found.


EDIT:  It said this exactly: "SP5100 TCO timer:  mmio address xfed000f0 already in use".

---

### Post by darkod on 2012-05-18
Sorry, my mistake. That's what happens when you try to help from the top of your head. :)

The parameter is:
b43.blacklist=yes

Sources:
One option is to disable wi-fi with the button, load ubuntu, blacklist the module and install another one:
[http://ubuntuincident.wordpress.com/2012/04/28/ubuntu-12-04-stops-booting-b43-wifi-problem/](http://ubuntuincident.wordpress.com/2012/04/28/ubuntu-12-04-stops-booting-b43-wifi-problem/)

Solution with adding the parameter so you can install ubuntu, and install the firmware later:
[http://ubuntuforums.org/showpost.php?p=11883375&postcount=6](http://ubuntuforums.org/showpost.php?p=11883375&postcount=6)

---

