---
title: "nvidia problem help"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by lafolla on 2008-04-26
hello
i have installed ubuntu 8.04
and i have some problem with screen
i ve a lcd samsung syncmaster 710n
and a graphic card nvidia geforce2 mx 400
i can see nothing i my screen
i can use only a old monitor crt with 800X600
please who can help me?

please...

---

### Post by Pumalite on 2008-04-26
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the driver. Then: startx

---

### Post by lafolla on 2008-04-26
i tried but cant configue video....
help please

---

### Post by hariprs on 2008-04-26
Try uninstalling the existing drivers and download the latest version from nvidia site and install. It worked for me.

---

### Post by chek2fire on 2008-04-26
Try to install the driver with envyng programme. You will find it in synaptic like envyng-gtk. If you have problems to run it open a terminal and type

> enyng -t

---

### Post by heiowge on 2008-04-26
I had a similar problem with a geforce 6 card.

I got past it by booting in safe graphics mode then installing the restricted drivers when prompted.

---

### Post by NEUR0M4NCER on 2008-04-26
> **Pumalite said:**
> sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the driver. Then: startx

Dude, as far as I can tell, that command doesn't work any more in Hardy, thanks to the new xorg's desire to try to configure everything automagically... It'll ask about keyboard n mouse, then kick you out again.


Regards

---

### Post by Pumalite on 2008-04-26
You are right. I just tested it. Normally I install my drivers and let them configure xserver.

---

