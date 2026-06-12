---
title: "installed ATI drivers now Ubuntu is DEAD"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by fatray on 2006-07-24
First off, just installed Ubuntu yesterday, I'm a total newb with Linux.
Installed Automatix.

Now the ATI drivers, was told to follow this.  [Installing the driver (ATI)]("http://doc.gwos.org/index.php/DapperGuide#Installing_the_driver_.28ATI.29")
Did it, not knowing what I was doing at all not a clue.  Just following the guide.  

> Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!
What is this, how do I make sure?

After entering each line one at a time, waiting for it to do what ever it was doing. I reboot.
Now I am greeted with the message:
> Failed to start the  X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?  "yes" "no"

I can't select yes or no.  It does ask me to login to desktop.  I do, now I'm at "fatray@fatray-desktop:~$"

What next?:confused: 

The graphics card is a built in RAGE PRO TURBO AGP 2X in a HP Pavilion 8390

---

### Post by Paerez on 2006-07-24
well if you want to get it back to square 1, you can always do the following:

Save your current setup in case you want to try again
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
```
then reconfigure:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
if you dont know the answer to any of the prompts, just hit enter, it will put the default.

ATI is an expletive to get working :(

---

### Post by NemesisUK on 2006-07-24
With the ATI card you have, the driver that was suppied with Ubuntu would of been better. Just edit /etc/X11/xorg.conf find Device "fglrx" and replace fglrx with ati and all should be fine again.

Nemesisuk

---

### Post by Schadenfroh on 2007-11-17
Thanks Paerez, your post saved me from a reinstall.  I am a complete linux newbie and when I tried to install the "restricted ati driver" in ubuntu 7.10, once it tried to load gnome (I assume, after the ubuntu progress bar reached completion), the display just went black and never recovered.  That command allowed the generic driver (does not even say ATI) to load and now I can at least get back to my desktop.

---

