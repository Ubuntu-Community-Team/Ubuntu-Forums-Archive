---
title: "fiesty is being a very bad fox"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by oxyrosis on 2007-04-25
so i updated to fiesty as my primary, and lo and behold it broke. well, not so much broke as it stopped working correctly. 

I rebooted my computer as you do, and when the login screen should have shown itself, i get a blank screen, i can see my mouse cursor which is in a permanent "hourglass" or "thinking" mode. i can CTRL+ALT+F1 to get to the text based mode...but being such a new user, this only causes me further grief.

i suspect it has something to do with my gdm or whatever that may be. 

ALSO, i dont know how to edit anything or really navigate anywhere on the command line, so a nice baby steps method would be most appreciated.

---

### Post by taurus on 2007-04-25
Boot into recovery mode from GRUB menu and reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
```
If you are not sure about a question, just use the default and use **vesa** driver for your graphic card for now until you get X running again.  Then, install the right driver for your graphic card.

---

### Post by oxyrosis on 2007-04-25
will do, be back after i restart..

thanks.

---

### Post by oxyrosis on 2007-04-25
well, i followed what you said to no avail.

i selected defaults for everything and vesa for the driver. now i get the same symptoms, just at a lower resolution.

blank screen, mouse constantly on "loading"

thoughts?

---

### Post by oxyrosis on 2007-04-25
i have to go to work now, i'll be back in around 7-8 hours

adios

---

### Post by SIZABANTU on 2007-09-14
I also have the same issue. I installed kdm and every thing worked. :) . but now i want to use vnc and cannot get to the settings i need.

---

