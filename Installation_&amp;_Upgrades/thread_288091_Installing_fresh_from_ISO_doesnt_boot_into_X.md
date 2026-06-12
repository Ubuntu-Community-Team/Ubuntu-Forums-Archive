---
title: "Installing fresh from ISO doesnt boot into X"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by aparsons on 2006-10-29
I have a new box that I'm trying to bring up on Edgy 6.10.  It has a 120GB, 512 RAM, Hauppauge PVR-350, ATI Radeon PCI 8500 AIW.

When I boot from the live CD of Edgy, I get to the screen and press ENTER to install Edgy.  Then, it loads everything it needs from the live CD, a black screen with a cursor in the top left appears, and then the screen goes grey (doesn't turn off the monitor).  I tried 2 ISO images with the same result.

This is driving me nuts.  Has anyone else had this problem?  Can I somehow install ubuntu without X, and then fix X later since that appears to be what the problem is?

---

### Post by nbx909 on 2006-10-29
yes use the alternate install instead. the computer can't handle the gui and the live cd asking for the 512 mb of ram

---

### Post by taurus on 2006-10-29
You have two options.  

1.  Try using alternate CD which is the same as LiveCD except it allows you to install it directly to your machine using text base.

2.  Use the server version and install Gnome later with

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```
So, try the alternate CD first and if it still doesn't work, then try the server version...

---

### Post by aparsons on 2006-10-29
Do you have a link to the alternate install?  Why wouldnt 512MB Ram be enough?!?!

---

### Post by aparsons on 2006-10-29
Sorry... posted too fast.

---

### Post by taurus on 2006-10-29
[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by aparsons on 2006-10-29
argh.  so i got past the install, but when ubuntu loads, I get a "grey" screen again.  How do I exit X and get to a terminal prompt to fix this ATI/X crap.

---

