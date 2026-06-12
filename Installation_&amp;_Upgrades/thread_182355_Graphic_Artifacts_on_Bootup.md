---
title: "Graphic Artifacts on Bootup"
date: 2006-05-25
forum: Installation &amp; Upgrades
---

### Post by ripkirby on 2006-05-25
Hello, I have been trying to boot up ubuntu 5.1 (64 bit and the 32 bit versions) on my system. I have tried live and installing ubuntu, both times giving me artifacts on the screen. I cannot see or do anything when it is like this. Any ideas what is wrong because i have no idea.

The artifacts take up the whole screen. I do not even reach the login screen. I tried installing server base only. When I did, I got to command line with no problems, but I do not wish to use command line only..

AMD X2 3800, 6800 GS, 1GB Ram, 80 Gb

---

### Post by richbarna on 2006-05-25
Hi ripkirby,
What exactly do you mean by "artifacts"?
Also, when you did the server install, in the terminal (using command line) you could have downloaded a desktop environment like KDE.
By typing this :-
> sudo apt-get update
> sudo apt-get install kde
This will then procede to download and install the desktop GUI.

---

### Post by ripkirby on 2006-05-25
Um, by artifact I mean like.. massive graphic screw up.. glitch.. it takes up entire screen. Some people get it by overclocking their video card to hard.. but that's not the case right now.

---

### Post by confused57 on 2006-05-25
It may be a problem with the video graphics driver Ubuntu automatically assigned for your video card.

Press Ctrl+Alt+F1 , which will get you to a text command prompt.

Enter:
```
sudo /etc/init.d/gdm stop
```
at the prompt, type in your password, then press "enter"

Enter:
```
sudo dpkg-reconfigure xserver-xorg
```
This will bring an interactive menu to configure your xserver, try changing the driver to "vesa", if this doesn't work, try "nv".  You may also want to make sure the screen resolutions listed are supported by your monitor, if not, you can change them

When you're finished configuring xserver-xorg, enter:

```
sudo /etc/init.d/gdm start
```

Edit: You'll probably have to login first, after pressing Ctrl+Alt+F1...

---

### Post by ripkirby on 2006-05-26
Nope not working.. I'm gonna try apt-get dist-upgrade. See what happens.

Update.. no luck.

Maybe I will try SuSe.

---

### Post by ripkirby on 2006-05-26
I tried SuSe, the image display on the screen is messed up still. Is it bad drivers??

---

