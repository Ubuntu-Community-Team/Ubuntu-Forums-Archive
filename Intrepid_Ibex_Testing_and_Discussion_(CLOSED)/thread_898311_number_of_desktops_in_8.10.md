---
title: "number of desktops in 8.10"
date: 2008-08-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by greyghost60 on 2008-08-23
Running 8.10 alpha 4 in Appearance 'normal' mode i get the usual 4 desktops but in extra mode I only get 2. Using Nvidia GeForce 8400 GS with 512meg memory and the 177.68 driver. The machine has a dual boot with 8.04 as the other boot and that works fine. Any ideas?

Greyghost

---

### Post by gjoellee on 2008-08-23
you can enable 4dekstops en several ways, here are one of them:

1. Do you have Compiz Fusion installed? It is available as a "one click install" from my website. Here is the direct link [http://kshoster.net/?c=downloads&h=apturl](http://kshoster.net/?c=downloads&h=apturl)

2. In Compiz you have to go to "general options" and to the "desktop size" tab. Then set the "horizontal value" to 4

3.If you want a cube enable "Desktop Cube" and "Rotate Cube" and then after that you may need start compiz.

4. Click on ALT + F2 and add this code
```
compiz --replace
```. If you want Compiz to start on startup go to System->Preferences-> Sessions and click on "add" and fill in a name, and at commands add the code above, and then click OK.

---

### Post by Gina on 2008-08-23
I have mine set to 8 using Preferences from the right-click. If I set Appearance to Extra mode it goes down to 4.  Just tried it at 6 and it still goes to 4 in Extra mode.  Graphics is ATI Radeon X740XL no proprietary driver.  I'm not running Compiz.  Strange and definitely a bug I would say.  I'll be interested in what others have to say on this. .

---

### Post by greyghost60 on 2008-08-23
Hi 
Yes I have compiz installed and everything works. It just the number of desktops 2 no matter what I put in the preference field. Is there a .conf file I can edit?

---

### Post by cjm5229 on 2008-08-23
You have to set the number of desktops in the CompizConfig Settings Manager. If you don't have it installed you can find it in Add/Remove. If it is installed it will be in System> Preferences, once you bring it up you can click on the "General Options" button.  From there go to the "Desktop Size" tab, The Virtual Horizontal Size Slider is where you set the number of desktops. When ever you have the Extras button enable in Desktop Effects you are controlling your desktop with Compiz, and everything will be controlled by the settings in CCSM. Gina, Compiz is installed by default now and the Desktops effects will enable it anytime you check anything other than "None". If it allows you to check "Extras" you must have a driver for your video card installed.

---

### Post by Gina on 2008-08-23
The Settings Manager puts itself too high on the screen and the top is out of sight so I can't check thaat.  It might be graphics card driver problems I guess.  It's an ATI Radeon X640XL - the proprietary driver refuses to work with it.  I'll check it ou on my AMD64 machine later - that's got nvidia graphics and the 177 driver works fine with it.

---

### Post by greyghost60 on 2008-08-23
Mnay thanks it works now, but 20 desktops???? :-)

---

### Post by cjm5229 on 2008-08-24
> **greyghost60 said:**
> Mnay thanks it works now, but 20 desktops???? :-)

:lolflag: That would be a bit much for me too! I'm a truck driver, I'm lucky I can count to 4, Like I always say, If I could count I would be an Engineer, not a Truck Driver. 

Gina, Since last nights updates, I can't get Nvidia drivers to work either, I am Compizless for now. I see we might be getting a new kernel, 2.6.27 soon, maybe that will fix it. I just spent the last hour trying to get it working, without success,  so I guess I will boot back into Hardy, and try later.

---

### Post by Gina on 2008-08-24
Ah well... that's the joy of running development software :lolflag:

I do rather enjoy being at the cutting edge :)

---

### Post by Hire on 2008-08-24
I had disabled Compiz for now, is too unstable :(

However, Metacity with composite is very nice to see :)

---

### Post by cjm5229 on 2008-08-24
Me Too, excuse me I need a new box of Band Aids.

---

