---
title: "can't change resolution in 7.10"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by yaywoop on 2007-11-01
I just booted 7.10 from the cd after having a 7.06 install
after booting with the cd, it doesn't recognize my resolution correctly and it doesn't want to change.
the resolution is at 1280x768. I need 1280x1024
I tried using system>preferences>screen resolution, to change it to 1280x1024. it just makes the screen flicker a few times but not actually change 
and system>administration>screens and graphics doesn't do anything either even when i try to select a different lcd

my previous 7.06 install recognized and worked with everything perfectly. 7.10 seems like a step backwards in compatibility.

---

### Post by etxkesa on 2007-11-01
You didn't say which graphics card you had. I had the same problem with mu Nvidia card, but once I downloaded the restricted drivers everything worked and I can now set the resolution to the same one you need. Try to see if you can find a dedicated driver.

---

### Post by davekayll on 2007-11-01
> **etxkesa said:**
> You didn't say which graphics card you had. I had the same problem with mu Nvidia card, but once I downloaded the restricted drivers everything worked and I can now set the resolution to the same one you need. Try to see if you can find a dedicated driver.
my resolution on feisty was 1280*1024 now its 800*600 since upgrade and i cant change it. my card is nvidia g-force 7600gs.
dont want to do install and lose data.
anyone got fix in plain language?

---

### Post by mcmilner on 2007-11-01
> **yaywoop said:**
> I just booted 7.10 from the cd after having a 7.06 install
after booting with the cd, it doesn't recognize my resolution correctly and it doesn't want to change.
the resolution is at 1280x768. I need 1280x1024
I tried using system>preferences>screen resolution, to change it to 1280x1024. it just makes the screen flicker a few times but not actually change 
and system>administration>screens and graphics doesn't do anything either even when i try to select a different lcd

my previous 7.06 install recognized and worked with everything perfectly. 7.10 seems like a step backwards in compatibility.

This is the command I used to change my screen resolution.  sudo dpkg-reconfigure -phigh xserver-xorg
If you want to see the background and what else I did, here is the [original thread]("http://ubuntuforums.org/showthread.php?t=432634") where I got the advice.

---

### Post by yaywoop on 2007-11-02
thanks for your help everyone. I think i will stick with 7.04 on my laptop. it just seems generally incompatible with 7.10 and 7.04 is working fine. btw the laptop used the open ATI drivers.
I did get it to work on my main pc though, which is ATI as well just be mucking around with the gui configuration utilities.

---

