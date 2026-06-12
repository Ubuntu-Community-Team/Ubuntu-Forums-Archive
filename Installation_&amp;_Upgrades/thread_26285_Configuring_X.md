---
title: "Configuring X"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by txwylde on 2005-04-12
I go through the install of Ubuntu and when it goes to restart and go into X, I get a black screen. Is it possible to configure X instead of having Ubuntu do it for me?
Thanks!
Bill

---

### Post by alexp on 2005-04-12
txwylde,

to get on a console, press <CTRL>+<ALT>+<F1>. On the console, login and type
 ```
sudo dpkg-reconfigure xserver-xorg
```
and follow the instructions.

Regards,
Alexander

---

### Post by txwylde on 2005-04-12
Thanks for the update. I am going to remove the old SIS card and replace it with another card and then try to configure X again. I have the settings that seem to work with X. Ironically, the live CD works without a problem. When I try to install it, I run into major issues. Ubuntu did find my wifi network and did install the drivers for it with out a problem.

---

### Post by txwylde on 2005-04-14
Weird thing is both Kubuntu and Ubuntu both do not like my display card. I have a old 3DFX 16 meg card. I replaced it with my SIS 16meg PCI video card and still ran into problems. It seems as when it goes to install the Fonts and files for X it fails then freezes and nothing happens. I try restarting and it does the same thing. Mandrake 10.1 works fine with it as does Xandros. I am a bit confused as to why the install is causing me so much grief.

---

