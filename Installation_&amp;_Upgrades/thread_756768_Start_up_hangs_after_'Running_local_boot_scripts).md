---
title: "Start up hangs after 'Running local boot scripts)"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by SteveAN on 2008-04-16
I have installed 7.10 and everything seemed to go well. Very easy install. 

However when the server starts it gets to 

* Running local boot scripts (/etc/rc.local)    [ OK ]

then hangs.

If I hit return I can login, but it's at command line and not GUI. I don't know enough about linux yet to know how to progress from here to what I would consider a workable machine.

Can someone please advise me......

---

### Post by Partyboi2 on 2008-04-16
What graphics card are you using?

---

### Post by redbob on 2008-04-16
SteveAN, by definition, the Server Edition of Ubuntu doesn't install of load Xserver, so no Gui was loaded. See this link: [http://ubuntuforums.org/showthread.php?p=2328506](http://ubuntuforums.org/showthread.php?p=2328506)

---

### Post by kerouac888 on 2008-04-16
I am also having this 'Running local Scripts problem'. Have looked all over and found various solutions. Namely, running dpkg-reconfigure xserver-xorg and fidddling about with the graphics driver and monitor resolution. I can't seem to get it to work and it doesnt seem to have any effect no matter what i do. (I have installed the alternate 7.10). Thanks for any help you can give me.

---

### Post by SteveAN on 2008-04-16
> **Partyboi2 said:**
> What graphics card are you using?

I'm installing in a VMware machine. I believe this is whatever the default it. I don't loose any graphics though. Other threads I've seen seem to expect the screen to go black if the graphics card is wrong. I am left with the list of steps to taken to get here.

---

### Post by SteveAN on 2008-04-16
> **redbob said:**
> SteveAN, by definition, the Server Edition of Ubuntu doesn't install of load Xserver, so no Gui was loaded. See this link: [http://ubuntuforums.org/showthread.php?p=2328506](http://ubuntuforums.org/showthread.php?p=2328506)


That's nuisance. I was installing it so I can put NistNet on it. 

How do I get a GUI on it?

---

