---
title: "Unable to Start X (Failed for Driver 0)"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by ozanamn on 2011-02-01
Hello All,

I have just run a fresh install of Kubuntu on an old PC to try it out for a few weeks. 

The Boot CD works fine and there is a GUI for the install. It seems to detect all the devices without a hitch. But when the PC reboots it boots into command line. When I try to run startx it gives me 

"AddScreen/ScreenInit failed for driver 0"

I looked up the x.org website and in the FAQ [Here]("http://wiki.x.org/wiki/FAQErrorMessages#Ikeepgettingthemessage.3A.22AddScreen.2BAC8-ScreenInitfailedfordriver0.22") it says 

"This kind of problem typically occurs when you're using a big monitor with an old graphics card. You can solve it by deleting some of the highest resolutions of the deepest colour mode in the Screen section of your xorg.conf, or even the whole last Display subsection."

I am using an old pc with old graphics card with a 25inch HP LP2465 monitor. 

in my /etc/X11 there is only a xorg.cof.failsafe file.  

anyone any ideas on how to do this. 

The full error is attached in a very bad screenshot. 

Cheers,
Oz



The Graphics Card is nVidia Corporation NV5 [RIVA TNT2/TNT2 PRO] (rev 15)

---

### Post by ozanamn on 2011-02-01
Bump!

---

### Post by ozanamn on 2011-02-02
Bump

---

