---
title: "Ubuntu Live USB Display Driver Problem"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Heero_Yuy_X on 2009-12-06
Hi guys, I have a problem after installing Ubuntu on a USB Pen Drive...

I used a tutorial and a script from this site to install it "www.pendrivelinux.com" persistently...

Compiz didn't work at first, and when I try to install the proprietary drivers, the Ubuntu splash screen shows weird colours. Though I'm back on the desktop normally, when I choose desktop effects I'm restricted to Low effects, since the Driver is somehow not properly installed... and Compiz functions like the desktop cube don't work...

I have an ATI HD4850 GPU btw, I already posted a forum a while back, but the only solution was to just install it normally on the Hardrive... and Ubuntu worked flawlessly...

I'm curious as to why it doesn't work normally on the Pen Drive too???

Any help appreciated...

---

### Post by darkod on 2009-12-06
I have not tried to install it like that on a stick and I don't know whether it keeps the drivers or not after shutdown. Otherwise, you could try installing EnvyNG package. You can find it in Software Centre or with:
sudo apt-get install envyng-core envyng-qt

It will be in Applications. That package handles video drivers and you can install different driver for the ATI with it if it's needed.

---

### Post by Heero_Yuy_X on 2009-12-06
Yea did that before, somebody in the previous forum I posted suggested that, but that doesnt work either...

I don't understand why the drivers can't be saved normally despite making the installation persistent...:-(

---

### Post by darkod on 2009-12-06
It might be a limitation of having LiveUSB.
Another option if you actually want to run it from the stick, is to install it there. Not with "permanency LiveUSB" but to actually install Ubuntu to the stick as location. But takes much more space then the 700MB the image takes. Minimum 2.8GB or similar.
But people have been installing on usb sticks/hdds and it's working fine. Then it will be like a real install and keep all software and drivers that you install.

---

### Post by jeyaganesh on 2009-12-07
Yes, I have installed ubuntu like 'darkod' suggested here. Heero_Yuy_X, I think you have better Graphic card than mine (Intel Graphics Controller 64MB).

Try to install ubuntu on USB as like on harddisk. During installation choose the usb stick instead of harddisk. As I have mentioned in another thread, I used 4GB USB (3.5GB for installation and 500MB for Swap).

---

### Post by Heero_Yuy_X on 2009-12-07
Great !!! I just tried it, never thought it would regard the USB as an HDD !!! :D
The driver is working awesome, Ubuntu is a bit slower than the one I have on the laptop, but I guess I shouldn't be greedy :p

Thanks alot for the advice guys ;)

Marking thread as solved...

---

