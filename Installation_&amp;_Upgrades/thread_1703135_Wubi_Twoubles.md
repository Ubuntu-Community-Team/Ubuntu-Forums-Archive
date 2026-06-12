---
title: "Wubi Twoubles"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by bourgtai on 2011-03-08
Okay, so I tried installing Ubuntu on its own partition a few days back, but because of a very aggravating trial with my Broadcom 4306 card and an utter inability to get it to connect despite several help threads on the matter, I went back to Windows.  Then I installed Ubuntu through Wubi.  Now, however, I have a new problem: when I load Ubuntu and login normally, the only thing that comes up is this:

Edit: (see attachment)

I tried running recovery mode and repairing broken packages (and there turned out to be a lot waiting for upgrades) and then reloading, but nothing changed.  Then I booted Ubuntu into Safe Mode, which actually brought up the desktop.  How does one fix this?  Or is there no disadvantage to defaulting to safe mode?

---

### Post by bcbc on 2011-03-08
Is this 10.10 netbook edition? If so, then you probably can't support Unity (the default desktop with Netbook). When you click on your username at the login screen, check what the session is set to (bottom of the screen) and if Unity, change it to Gnome desktop.

---

### Post by bourgtai on 2011-03-09
Hey there,

No, it's the traditional Ubuntu desktop (the safe mode has the same name except with 'safe mode'  appended).  And I know that my laptop normally supports it, because it used to display fine when I did a traditional install.

Thanks for the quick reply!

---

### Post by bcbc on 2011-03-09
hmm. maybe you need to download a specific driver for your graphics card... which card do you have? If you boot in safe mode and go to System, Administration, Hardware drivers - and see if it suggests some drivers.

---

### Post by bourgtai on 2011-03-09
Sadly, it only suggests a driver for my wireless card, which... I'm trying to fix in a different way.  Hmm... I really thought that could be the problem.

EDIT: According to lspci, my VGA controller is an ATI Radeon Mobility U1.

---

### Post by bcbc on 2011-03-09
This thread *may* have the solution: [http://ubuntuforums.org/showthread.php?p=10244806](http://ubuntuforums.org/showthread.php?p=10244806)

---

