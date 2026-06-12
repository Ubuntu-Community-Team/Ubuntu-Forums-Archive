---
title: "karmic on tablet computers - evtouch calibration"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrew frank on 2009-10-04
i installed karmic beta on a fujitsu p1630 with a touchscreen. it worked out of the box (nearly) - which is amazing. the stylus was recognized and worked (only poorly calibrated). missing:
calibration - i installed touchscreen calibration (from add applications) and run it, but it seems not to produce the right data. copying /etc/evtouch/config from my working 9.04 installation did eventually help - it took several restarts. 
i do not understand how and when evtouch reads in the calibration files. i also lack understanding what the parameter ein evtouch/config mean. could somebody point me to the documentation?
why is the calibration not read in and used immediately after completing the calibrtion routine and a restart required? this is awkward and error prone (i have the impression it is not always done)

thank you
andrew

---

### Post by andrew frank on 2009-10-04
i installed karmic beta on a fujitsu p1630 with a touchscreen. it worked out of the box (nearly) - but i cannot get the buttons around the screen to work. the recommendations on the web to edit X11/conf or HAL policies seem not to be the way karmic solves this.
how are buttons (e.g. to rotate the screen) to be added to karmic? is there any documentation or examples one could copy from?

i used xev to see the events created by the buttons - no event created. what is necessary to have the buttons recognized?

thank you
andrew

---

### Post by Favux on 2009-10-04
Hi andrew frank,

Since it is a Fujitsu it may use the "fjbtndrv" driver for the bezel buttons.  See posts #15 and 16 here:  [http://ubuntuforums.org/showthread.php?t=1259154&page=2](http://ubuntuforums.org/showthread.php?t=1259154&page=2)  But I don't know if this will work in Karmic.  You may have to try and compile it from source.

---

### Post by Favux on 2009-10-04
Hi andrew frank,

The articles on the Fujitsu p1630 say it has a passive touchscreen.  They do not say who makes it.  So I'm not sure "evtouch" is the right driver.  Plus you are using Karmic, so not much information yet.

If evtouch is the correct driver see:  [http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html)  From here:  [http://www.conan.de/touchscreen/](http://www.conan.de/touchscreen/)

If it is a eGalax touchscreen see post #29 here:  [http://ubuntuforums.org/showthread.php?t=1040872&highlight=tx1000&page=3](http://ubuntuforums.org/showthread.php?t=1040872&highlight=tx1000&page=3)  The link for the driver he gives takes you here:  [http://home.eeti.com.tw/web20/eGalaxTouchDriver/QNXDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/QNXDriver.htm)

This HOW TO describes using Touchkit to calibrate:  [http://kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Touch_Screen](http://kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Touch_Screen)  But it is old.  If adding entries is xorg.conf is needed perhaps they can/should be moved to a fujp1630.fdi or evtouch.fdi?  Another old thread you could search for calibration:  [http://ubuntuforums.org/showthread.php?t=442483](http://ubuntuforums.org/showthread.php?t=442483)

Hope this helps.

Edit:  Found someone developing a Fujitsu usb touchscreen driver.  Says it works for the p1630.  Has a python applet for calibration.  Here:  [http://spareinfo.blogspot.com/2009/05/linux-on-u810-p1620-touchscreen-iv.html](http://spareinfo.blogspot.com/2009/05/linux-on-u810-p1620-touchscreen-iv.html)  From here:  [http://spareinfo.blogspot.com/2009/08/linux-on-fujitsu-u810-p1620-p1630-t1010.html](http://spareinfo.blogspot.com/2009/08/linux-on-fujitsu-u810-p1620-p1630-t1010.html)  Again, who knows if this will work in Karmic.  But it's from July of this year.

---

