---
title: "Wireless Driver Installation"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by btpoole on 2012-08-13
Really new to all things not Microsoft.  I have installed Ubuntu 12 on a laptop to see how I like it.  For some reason my wireless connection will connect to router and states it's connected but it will not browse the internet.  I feel I need to install a driver for the wireless device.  I have downloaded ndisgtk to install.  When it attempts to install it wants to be placed where my inf files are located.  I don't mean to sound dumb but I have no idea where to find them in Ubuntu. Windows no problem, but I am at a loss here.
Thanks for any help.

---

### Post by Moose on 2012-08-13
I had the same problem, trust me, The drivers for wireless are basically rare or nonexistant. I found a way to get it to work. You can either connect to your wifi through hidden netwrok settings. And if you have plenty of credit and can risk having wifi stolen you can also take the password off of your wifi. both of these methods worked for me. If all else fails just connect your router to your pc with an ethernet cable or whatever. I also found that if you plug an android phone into your pc via usb and then enable tethering in network settings (on phone) then you can browse using your phones internet credit. But make sure you are on a plan where you have lots or onlimited web browsing because your pc will drain credit super fast off of phone.
 
Be sure to PM me if you find a better solution or if mine worked for you
-Anarchy

---

### Post by CharlesA on 2012-08-13
> **btpoole said:**
> Really new to all things not Microsoft.  I have installed Ubuntu 12 on a laptop to see how I like it.  For some reason my wireless connection will connect to router and states it's connected but it will not browse the internet.  I feel I need to install a driver for the wireless device.  I have downloaded ndisgtk to install.  When it attempts to install it wants to be placed where my inf files are located.  I don't mean to sound dumb but I have no idea where to find them in Ubuntu. Windows no problem, but I am at a loss here.
Thanks for any help.

Are you able to verify you are actually connected? Can you ping the router's IP address?

Can you run this please:

```
ifconfig
```

> **AnarchyTech said:**
> I had the same problem, trust me, The drivers for wireless are basically rare or nonexistant. I found a way to get it to work. You can either connect to your wifi through hidden netwrok settings. And if you have plenty of credit and can risk having wifi stolen you can also take the password off of your wifi. both of these methods worked for me. If all else fails just connect your router to your pc with an ethernet cable or whatever. I also found that if you plug an android phone into your pc via usb and then enable tethering in network settings (on phone) then you can browse using your phones internet credit. But make sure you are on a plan where you have lots or onlimited web browsing because your pc will drain credit super fast off of phone.
 
Be sure to PM me if you find a better solution or if mine worked for you
-Anarchy

Wireless is hit-or-miss. It all depends on what chipset your wireless card uses. I have tested Ubunutu on three different laptops and have had no problems with wireless.

You really should not disable any wireless security. That opens a whole other can of worms and I have not seen a wireless card that needed to connect to an unsecured access point.

---

### Post by btpoole on 2012-08-14
Thanks for the replies and suggestions.
 
I can run iconfig and get my int addr back along with that of the router.  The router is a Linksys used in my home.  I have several other computers that accecss it both with cable and wireless.  I have no secutiry set up on it.  My closest neighbor is approx.  1/2 mile. Not worried about security at this point.  Odd thing, when I first installed Ubuntu I installed 10.04.  I was able to connect with wireless deveice but it would go out after a while.  I upgrade to 12, not passing each version between them.  I thought maybe 12 had the problem fixed.

---

### Post by btpoole on 2012-08-14
WEIRD.   I connected to hidded wireless network, actually same one I was connecting not but not hidded and it connected right away.  Runs fine.  I really don't understand this one.

---

