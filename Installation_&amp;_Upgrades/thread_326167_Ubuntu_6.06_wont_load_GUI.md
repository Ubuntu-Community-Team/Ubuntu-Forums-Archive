---
title: "Ubuntu 6.06 wont load GUI"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by RaiFox on 2006-12-27
I've recently upgraded my graphics card to an AGP GeForce 7600 GS (from a Radeon9550), and when loading Ubuntu I encountered a dos-looking dialog box that basically said the GUI wont load.

No big loss because I'm still getting used to Ubuntu and don't use it for anything serious, I just assumed it had something to do with my graphics card being changed and so I formatted my HDD.

So I found my Ubuntu installation CD and booted up my PC, I went to the "Start or install Ubuntu." menu option, after loading I encountered a box claiming that the GUI couldn't be loaded also on the screen was miscellaneous text and a command prompt.

So I tried the limited graphics option, the result was an improvement but still a long way off from anything usable, it was a black screen with an X symbol in the middle of the screen which could be controlled with the mouse.

I'm assuming this problem has something to do with my graphics card, because it was working fine with my Radeon9550.

I'm using Ubuntu 6.06

I'm somewhat of a newb with Ubuntu, so please take that into account when replying.

---

### Post by bulldog on 2006-12-27
Try the alternate cd which has a text based install.
This one works better than the live cd.

FYI,you only had to install the nvidia driver for your graphics,it would have removed the ATI driver.:-)

---

### Post by RaiFox on 2006-12-27
Would using the "alternate CD" actually work, because when I loaded a normal-CD installation off the HDD it gave the same error as the live-cd.

So if the alternate CD installs the same thing as the normal one wouldn't the outcome be the same?

---

### Post by confused57 on 2006-12-28
> **RaiFox said:**
> Would using the "alternate CD" actually work, because when I loaded a normal-CD installation off the HDD it gave the same error as the live-cd.

So if the alternate CD installs the same thing as the normal one wouldn't the outcome be the same?

Yes, most problems you encounter with the live cd will also occur with an installation.  Here's an excellent link to reconfiguring your xorg.conf:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

If you're getting the "box" with the message that the xserver could not be started, then you can use the above link to reconfigure...try using the "nv" driver or "vesa" driver.
This is an interactive way of configuring your xorg.conf file & you'll mainly be interested in selecting the "nv" driver.

Also, when your get the error message or the "X" you can move with the mouse...you could press:   Ctrl+Alt+F1     which opens a console, login.

```
sudo /etc/init.d/gdm stop
```

then you can enter:
```
sudo dpkg-reconfigure xserver-xorg
```

or you can manually add the driver to your xorg.conf file:
```
sudo nano /etc/X11/xorg.conf
```
go down to the video device section & change the driver to "nv" or "vesa"
Ctrl+X, Y, enter to save changes.

```
sudo /etc/init.d/gdm start
```
to restart your GUI...or just **startx **may work.

This will give you some things to try, hopefully it'll work.

---

