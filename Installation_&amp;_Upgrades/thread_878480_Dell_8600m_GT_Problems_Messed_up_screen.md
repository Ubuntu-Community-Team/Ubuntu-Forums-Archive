---
title: "Dell 8600m GT Problems Messed up screen"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by korndog2003 on 2008-08-02
I have have a Dell Vostro 1500
Specs: 
Core 2 Duo 1.4Ghz
4Gb High Performance OCZ Memory
nVIDIA 8600m GT 256 MB

 I just installed Ubuntu 8.04 LTS Desktop Edition. I enabled the restricted nVIDIA Drivers and rebooted and this is what came up. This is the second time I have installed Ubuntu and this has happened, How do I fix the current installation and get the right drivers?

Thanks, Luke

---

### Post by Rocket2DMn on 2008-08-03
Hi, I edited your post so that there isn't that huge screenshot, I made it an attachment instead.

RE: Your problem
After you boot the computer, do CTRL+ALT+F1 to get to a TTY, login at this terminal, and run the following commands:
```
sudo apt-get remove --purge nvidia-glx-new
sudo dpkg-reconfigure xserver-xorg -phigh
sudo /etc/init.d/gdm restart
```
(I think you are using nvidia-glx-new, but if it doesn't like that first command, try nvidia-glx instead).
The GUI should now restart normally, with the restricted drivers disabled.  If it doesn't take you to the GUI, do CTRL+ALT+F7 and do CTRL+ALT+BACKSPACE to restart X.

This time, rather than using the Hardware Drivers manager to install the restricted drivers, you might give EnvyNG a try - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
This should detect the card and install the correct drivers for you.  After a system reboot you should be good to go.

---

### Post by korndog2003 on 2008-08-04
worked perfect thanks!

---

