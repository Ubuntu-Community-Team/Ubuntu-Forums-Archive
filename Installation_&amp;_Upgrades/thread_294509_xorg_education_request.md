---
title: "xorg education request"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by dxturner on 2006-11-06
I am seeing some behavior that I don't understand and was hoping someone could educate me.

I have an IBM T30 laptop running ubuntu 6.06 LTS.  I attached an external monitor to it and would like to run a resolution of 1280x1024.  The working xorg.conf file was configured with the ati driver (the video card is ATI Mobility Radeon 7500), but when I modified the xorg.conf by changing:

Mode     "1024x768"

to

Mode     "1280x1024"

the gdm login screen would come up and I could enter my username/passwd, but then I would immediately get dropped to a text login prompt.  I thought that perhaps the driver didn't support that resolution so I modified the Driver line from "ati" to "vesa".  No luck ... though I did get an X session ... at 600x480.  So, I tried "radeon".  No luck ... same behavior as "ati" driver.  Just for grins I tried "fglrx", which is what I use on my other IBM laptop with a different ATI card, and this time after logging in I get an "X configuration error screen" ... which says, basically, fix xorg.conf and restart X.  It gives me a text login, I login as root, edit xorg.conf and put "vesa" in place of "fglrx", save the file, and then do "startx"

X starts and the screen looks just like I want.  Neat, huh?  But I'm logged in as root.  So, I log out, log back in as a normal user and I'm back to my  original problem.

Sorry for the long description, but I suppose the question is, given the above scenario, can someone explain what is happening?  I'd like to understand it so that I have a chance at remembering the solution.  I figure if I can get it work the way I want as root, I should be able to get it to work for a normal user, but I don't understand the mechanics well enough to puzzle it out.

Thanks for any help.

---

### Post by taurus on 2006-11-06
Could be because your laptop monitor and your desktop monitor may not have the same refreshing rates!!!  Since your current /etc/X11/xorg.conf is configured for your laptop monitor, when you try to use it for your desktop, it bombs you right out.  Therefore, you need to create another /etc/X11/xorg.conf for your desktop monitor with

```
sudo dpkg-reconfigure xserver-xorg
```
And before you run that command, I recommend you save the current /etc/X11/xorg.conf to something like /etc/X11/xorg.conf.laptop.  Then copy the new /etc/X11/xorg.conf to /etc/X11/xorg.conf.desktop.  When you want to use your laptop monitor, just copy (not move) /etc/X11/xorg.conf.laptop to /etc/X11/xorg.conf and if you want to use the big monitor, then just cp /etc/X11/xorg.conf.desktop to /etc/X11/xorg.conf.

---

### Post by dxturner on 2006-11-07
Thanks for the reply, and I understand that I may need different xorg.conf to accommodate the different monitors.  I still don't understand why I can get it to work if I intentionally break it by loading the fglrx driver, editing it, and doing "startx" from a command line ... but then when the system reboots it doesn't keep those settings.  Has anyone got a simple overview doc of xorg.conf they can refer me to?

Thanks again.

---

