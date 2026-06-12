---
title: "black screen when rebooting pc after installing ubuntu"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by rubenosqui on 2008-02-23
Hello there, im new using Ubuntu
i just installed it yesterday
and everything was fine until i reboot my computer, everytime i restart my pc i got my dual boot screen because i also have xp pro if i choose to boot from xp i runs great but when i choose ubuntu all i get is a black screen not even ubuntu logo or username screen.
When i installed it i had the chance of installing my video drivers im using ATI X1300

please Helpp !!!!

---

### Post by taurus on 2008-02-23
Does it boot at all?  Maybe it boots but it can't start the GUI login screen.  If that's the case, press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, press <Alt>F7 and then <Ctrl><Alt>Backspace to restart X.

Or boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by sctech29169 on 2008-02-23
I had the same problem when upgrading to 2.6.22-14. I had to manually reconfigure through terminal the video card (GE Force 6400).

I do not have the notes on how I did it but if you ask, someone will know how.

Rodney

---

### Post by rubenosqui on 2008-02-23
hello, i tried as you said  ctrl alt F2 and enter 
sudo dpkg-reconfigure -high xserver-xoeg 

the it says necesary to select video card driver for x server i selected ATI since a have a ATI X1300

the appears /etc/x11/xorg.confi.20080223132620

restarted the computer and everything was the same after rebooting i got kernel alive
kernel mapping tables and then the black screen

i tried using recovery mode and exactly the same thing happened

---

### Post by taurus on 2008-02-23
Try the **vesa** generic driver to see if X runs at all.

---

### Post by rubenosqui on 2008-02-23
i tried using the generic VESA and i got the same black screen

---

