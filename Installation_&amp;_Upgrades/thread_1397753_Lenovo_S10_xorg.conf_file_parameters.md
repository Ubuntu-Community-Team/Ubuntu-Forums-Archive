---
title: "Lenovo S10 xorg.conf file parameters"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by kas65 on 2010-02-03
Hi all,

I am having a problem with my display, it's fuzzy and I can't see anything but lines. I rebooted using an installation usb key and was able to edit and modify /etc/X11/xorg.conf file. I tried several parameters regarding the display and still unable to get a clear screen. Could anyone with a Lenovo S10 running ubuntu remix please please send me a copy of the xorg.conf file. 

thanks,

kas

---

### Post by Jive Turkey on 2010-02-03
I have a lenovo s10e running ubuntu 9.10 (not remix).  I haven't made any adjustments to the display after installing ubuntu.  I have no xorg.conf file at all.

when I run lspci it shows these lines for my gfx chip:```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```
I'll do my best to get you through this.  Below is a screenshot of my (default) display settings.  Try renaming your xorg.conf to something else and restarting x.  AFAIK the xorg.conf file is optional.

Does your display work correctly if you drop to a shell (ie ctrl+alt+F2)?  If not, I'd recommend you just try either reinstalling or installing regular Ubuntu.  I haven't found it to be too cramped on the 10" screen at all.  You might consider the moblin version too.

I'll subscribe to this thread so I can remember to get back to it.  The lenovo website has a pretty active community forum too.  You might want to search over there too.

---

### Post by kas65 on 2010-02-03
Thank you so much for your help. Here are my comments:
. I have the same lspci output as yours.
. I renamed xorg.conf and restarted X but still not working. I still have two small Ubuntu logos with some garbage on the screen.
. Using ctrl+alt+F2 did not do anything.

The only way I can use my netbook since the problem began is to boot using an installation usb key.

Please let me know if I have any other options besides reinstalling. I can't believe that a small mistake halts the whole system. As a MAC guy it really frustrates me that everytime I have a silly problem I have to reinstall the OS and all the software.

Once again thank you for putting the time to help me.

kas

---

### Post by Jive Turkey on 2010-02-06
If ctrl+alt+F(n) doesn't drop you to a login there is likely a problem with your install at a deeper level than anyone can fix.  Have you checked the integrity of your installation media?  In any case, try the regular ubuntu, it works flawlessly on my s10.

---

### Post by kas65 on 2010-02-12
Thanks for your help. I reinstalled Ubuntu 9.04 and all is ok. I refrained from using an external monitor at this point. On the other hand, I upgraded to 9.10 and my system was very slow in all aspects, launching apps, browsing the net..etc so I reinstalled 9.04. Are you running 9.10 on your system and did you upgrade or installed from scratch? Also are you experiencing any slowness in comparison to 9.04? I have 2GB of RAM.

thanks,

---

