---
title: "Can't boot Linux because of gdm errors"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by Distortion1234 on 2007-11-01
After I choose the option to Install or Boot Ubuntu (or something of that nature), the progress bar loads to 100% and then I receive a few messages and the last one I get is:

* Running local boot scripts (etc/rc.local) [OK]

From there, the whole process just seems to hang and not go anywhere at all.

I get the following errors after hitting Alt + F1 and typing "tail /var/log/syslog"

gdm_slave_xioerror_handler Fatal X error - Restarting: 0
***Same thing repeated a few times***
Critical: gdm_config_value_get_bool:assertion `value -> type == GDM_CONFIG_VALUE_BOOL' failed

I've tried googling these errors (more so the first one) and searching these boards. I've found a decent amount of posts and such relating to them, and the main problem (or reason) for getting the first error seems to be associated with Firefox or a couple other things. Obviously, I can't even get so far as to install Firefox at this point, so I'm not too sure what to do from here and I haven't really seen any solutions for the Firefox/etc. related problem posts I've found anyway.

Here's my system specs:

x1 AMD Athlon XP 2900+ CPU / Socket A Soyo KT600 v2 motherboard
x2 1GB modules of Ultra PC3200 DDR Memory
x1 Maxtor 5400 RPM IDE Hard Drive
x1 Maxtor 7200 RPM SATA Hard Drive
x1 MSI nVidia GeForce 6600 GT (128MB)
x1 Some cheap, crappy PCI video card that I can't even remember much about

I've also tried adding "ide=nodma" and "acpi=off" to my boot parameters and that hasn't concluded with a positive result either.

---

### Post by Pumalite on 2007-11-01
If not a bad burn, try Alternate CD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Distortion1234 on 2007-11-01
I used the "check CD" option in the menu and it didn't find any errors. I'll try re-burning the image on a different disc at a slower speed, but I don't think that's the problem. Other than the reason I already mentioned, I also had this same problem with the previous version of Ubuntu and never really got around to trying to find a solution before the newest one was released.

---

### Post by Pumalite on 2007-11-01
Don't forget to do md5sum and compare it to the one posted by the site where you downloaded from. That's vital. So, if not a bad burn, then, you know: Alternate CD.

---

### Post by Distortion1234 on 2007-11-01
Well, the Alternate CD worked as far as the installation goes. Everything with smooth and it seemed to complete successfully. Nonetheless, the problem still continues and I can't get any farther than before.

The only difference this time is that when I hit Alt + F1 the screen will continue to blink (despite being at a different screen) and will end up just going blank.

---

### Post by Distortion1234 on 2007-11-02
Bump in hopes that someone has a solution. >_<

---

### Post by Distortion1234 on 2007-11-02
Not sure if it makes a difference, but the nVidia card I have listed (my primary video card) is an AGP version.

---

### Post by Pumalite on 2007-11-02
Were you able to finish the installation?

---

### Post by Distortion1234 on 2007-11-02
> **Pumalite said:**
> Were you able to finish the installation?

Yes, the installation completed without any errors. My problem is afterwards, during the boot process with the gdm errors still.

---

### Post by Pumalite on 2007-11-02
See if you can get a command line with:
Ctrl+Alt+F1
Then try:
sudo dpkg-reconfigure xserver-xorg

---

### Post by Distortion1234 on 2007-11-02
I'll try that first thing when I get home today.

I know I can get to a command line, because I did it yesterday after installing and having this problem. I had an additional problem at that point, though, and that was with the screen ending up just going blank. Hopefully, if that happens again I can still enter that command and get somewhere; I guess I just won't be able to see the output, heh.

Thanks for your help with all of this, and I'll post back here once I have some results.

---

### Post by Pumalite on 2007-11-02
Good luck.

---

