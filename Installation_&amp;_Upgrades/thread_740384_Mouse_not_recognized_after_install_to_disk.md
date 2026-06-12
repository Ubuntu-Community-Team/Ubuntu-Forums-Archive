---
title: "Mouse not recognized after install to disk"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by epiphanias on 2008-03-30
I just installed Ubuntu 7.10 from the live CD in February Linux Magazine. The mouse and keyboard worked fine while booted from the live CD, and during the install.  After reboot, Ubumtu comes up to the login screen, but the cursor does not respond no matter whether a PS/2 or USB mouse is attached.  There are no issues with the keyboard.  The mouse units I used to test work fine on other machines.

What can I do to fix?  

Thanks!
epiphanias

---

### Post by Pumalite on 2008-03-30
After boot, move your USB mouse to different ports. Let's see what happens.

---

### Post by programmer8922 on 2008-04-01
I had a similar thing happen after upgrading to gutsy. In order to get to terminal press Alt+F2 and start to type terminal -> the drop down list will get shorter -> select terminal -> click run -> run the following command:
```
dpkg-reconfigure xserver-xorg
```

---

