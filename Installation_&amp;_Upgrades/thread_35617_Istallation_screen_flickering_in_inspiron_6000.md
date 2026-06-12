---
title: "Istallation screen flickering in inspiron 6000"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by aeromaverick on 2005-05-19
hi

i am goin to install unbuntu for the first time on my new laptop inspiron 6000
i have installed many linux distributions on my desktop but never on a laptop...when i hit enter on the install screen.. the installer loads but then the screen starts scrollin fast and flickers.. i cant read what is on the screen to go to next step.. do i need to do some setting with my screen as it is 15.4 inch wide screen...plz help me...if ne one of u can..

aeromaverick

---

### Post by phatmaxx on 2005-06-04
Hi aeromaverick!

I also own an Inspiron 6000 Notebook ;)

On ubuntu-boot-menu enter the following: "linux vga=771", the 771 means that ubuntu will be installed on a notebook with tft screen.

This worked for me..

---

### Post by mingus on 2005-06-04
With a laptop it is absolutely critical to *not* use a video mode higher than what the display can support - otherwise, it might be fried.  Do not confuse what the video card or driver can support vs what the display can support.

Here are the values:

    | 640x480  800x600  1024x768 1280x1024
----+-------------------------------------
256 |  0x301    0x303    0x305    0x307
32k |  0x310    0x313    0x316    0x319
64k |  0x311    0x314    0x317    0x31A
16M |  0x312    0x315    0x318    0x31B

      640x480 800x600 1024x768 1280x1024
256 	769 	771 	773 	775
32K 	784 	787 	790 	793
64K 	785 	788 	791 	794
16M 	786 	789 	792 	795

771 is therefore the equivalent of disabling the framebuffer and using standard vga (that is, "vga=normal).

Also remember that the configuration for your graphical display is configured separately for the X-server.  Here it is critical you not exceed the refresh rates of the display.  Usually the probe handles all this for you, but not always.

---

### Post by aeromaverick on 2005-06-07
Thanks for the Help, Guys

venkat

---

