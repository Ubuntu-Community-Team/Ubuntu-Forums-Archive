---
title: "Upgrade to 7.04"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by liquidfunk on 2007-09-26
Something tells me I shouldn't have upgraded. Recently I decided it was time to upgrade.

 I did it through the update manager. 

 Went well, up until the restart.

 At which point, Xserver failurge/ error.

 Reconfigured it. I hear the sounds of the log on. 

 Then my monitor tells me that the imput is not supported?

 Help!

---

### Post by mikewhatever on 2007-09-26
You can try booting into recovery mode and opening xorg with 
> sudo nano /etc/X11/xorg.conf

Post the output here so that people have something substantial to work with.

---

### Post by liquidfunk on 2007-09-27
I have a better idea. Rather than tralling through code, possibly ending up with more problems?

 I think it would be better to copy my files onto my External HD, and re install. 

 However, problem 1. Some of my folders are Root protected. They have a Red and white cross on them which does not allow me to copy them, or even look at them. Common problem. This is by using the Live CD of Feisty.

---

### Post by Pumalite on 2007-09-27
Maybe all you need to do is reinstall your video drivers.

---

### Post by liquidfunk on 2007-09-27
How do I do that if I can't see anything?

---

### Post by Pumalite on 2007-09-27
We can fix that,but we first need to know your graphics and what drivers you had installed before.

---

### Post by liquidfunk on 2007-09-27
Nvidia Geforce2 MX400 64mb is my Graphics card.

 As for Drivers, I believe it was the Legacy driver, seeing as how old the card is.

---

### Post by Pumalite on 2007-09-27
Ctrl+Alt+F1 to get a command line
At the command line:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

