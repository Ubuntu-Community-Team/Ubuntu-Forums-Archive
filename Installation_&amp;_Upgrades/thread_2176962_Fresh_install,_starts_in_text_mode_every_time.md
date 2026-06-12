---
title: "Fresh install, starts in text mode every time"
date: 2013-09-26
forum: Installation &amp; Upgrades
---

### Post by alex106 on 2013-09-26
Hiya,

I just bought myself an [ACER V5 122P laptop]("http://www.pcworld.co.uk/gbuk/laptops-netbooks/laptops/laptops/acer-aspire-v5-122p-11-6-touchscreen-laptop-silver-21414700-pdt.html") and installed Ubuntu on it. The installation went fine, from what I can tell; I had the GUI interface, I could connect to wifi and move the setup windows around (even with the integrated touchscreen). The installation finished and the computer restarted.

Now every time I load up I just get what I can only assume is "text mode". I get a text prompt asking for my username and password and, when entering this, all I get is a command line. Nothing else. Could somebody help me troubleshoot this problem? I am assuming it is a display issue. If you didn't look at the link I posted, the GPU is a AMD RADEON HD 8210 :)

(And yes, I downloaded the desktop edition!)

EDIT: Sometimes, when I boot the machine up it does something different. It gets up to "Starting LightDM display manager", says [OK] beside it and hangs there indefinitely..

---

### Post by weyenk on 2013-10-08
My wife has the same problem on her Acer v5 122p.  I used 13.10 and got it to work but its unusable.  I read somewhere it had something to do with A6-1450 being an APU that is only used in this device.

---

### Post by heir4c on 2013-10-08
After login you can use the command:
```
startx
```

And what "Starting LightDM display manager" concerns: maybe you have trouble with that. Some have it to, so search for it on this forum of via Google. I have no experience with that.

I also have 13.10 here with a APU E-350 and that works fine. (with open-drivers and fglrx, without a separate graphics card)

---

### Post by baabsaget on 2013-10-08
Try entering your username (all lowercase) and password to log in.

Then enter these commands to re-install lightdm.

sudo apt-get purge lightdm
sudo apt-get install lightdm
sudo dpkg-reconfigure lightdm

If a window asks you if you want to use lightdm, say yes.

This solution may seem silly, but it happened to me once.

---

