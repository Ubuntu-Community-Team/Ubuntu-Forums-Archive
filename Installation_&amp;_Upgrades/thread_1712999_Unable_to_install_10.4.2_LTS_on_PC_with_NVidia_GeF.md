---
title: "Unable to install 10.4.2 LTS on PC with NVidia GeForce 6150 card"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by 39er on 2011-03-23
This is to request the communities assistance with the following:
As the title suggests, I am attempting to install 10.04.2 LTS on a PC equipped with an ASUS M2NPV-VM mobo and integral NVidia GeForce 6150 chipset/card and AMD dual processors.

Result: While the CD with the installation software loads, the splash screen comes up distorted and is displayed as several black and white horizontal bars. I have tried this with low end monitors with a VGA input with the same results.

It appears to me as if though the video driver on the installation CD is not suitable for the  mobo's chipset, but I may be wrong.

Your kind assistance would be appreciated.

Thank you.
-39er

---

### Post by Quackers on 2011-03-23
Welcome to UF.
When booting from the live cd and at the first purple screen press any key. Then choose your language and on the next screen press F6. Some options will appear bottom right. Select the "nomodeset" option and see if the cd can then boot to the live desktop.

---

### Post by 39er on 2011-03-23
> **Quackers said:**
> Welcome to UF.
When booting from the live cd and at the first purple screen press any key. Then choose your language and on the next screen press F6. Some options will appear bottom right. Select the "nomodeset" option and see if the cd can then boot to the live desktop.


Yes Sir Quackers, It booted nicely to the live desktop. Actual installation should be easy from here.

Thank you very kindly and nice meeting you here.

-39er

---

### Post by Quackers on 2011-03-23
You're welcome :-) Glad it helped.
Unfortunately that's not the end of it :-(
After installing, on the first boot you will need to enter the nomodeset option again, but in a different place. Details below.
After booting to the desktop go to System > Admin > Additional drivers and see if there is a nvidia driver available for your card, there probably will be. Install that driver and reboot, then you shouldn't need the nomodeset boot option again.

Scroll down to this section "How to temporarily set kernel boot options on an installed OS (not wubi)"
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by 39er on 2011-03-23
> **Quackers said:**
> You're welcome :-) Glad it helped.
Unfortunately that's not the end of it :-(
After installing, on the first boot you will need to enter the nomodeset option again, but in a different place. Details below.
After booting to the desktop go to System > Admin > Additional drivers and see if there is a nvidia driver available for your card, there probably will be. Install that driver and reboot, then you shouldn't need the nomodeset boot option again.

Scroll down to this section "How to temporarily set kernel boot options on an installed OS (not wubi)"
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I gratefully acknowledge your help. After some head scratching, low level formating the hd and reinstalling 10.04.2 LTS, I got the drift of the procedure. I nearly made a frisbee out of the mobo and install something more recent.
The O/S is now happily chugging along with crunching Worldcommunity Grid projects.

Regards,
-39er

---

### Post by Quackers on 2011-03-24
Very nice :-) Well done in persevering :wink:
Please mark the thread as solved using the Thread Tools near the top of the page. It may help other when searching. Thanks.

---

