---
title: "Wrong screen size after install (Lubuntu)"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by BADGER.BRAD on 2013-11-10
Hello all,
I have just installed Lubuntu on my daughters note book  (ASUS Eee PC) but only have one screen resolution available 800x600 I need 20240x600 any ideas what I can do ? Would I be any better with Xubuntu or should I just install XP

Many thanks all

---

### Post by TheFu on 2013-11-10
I have an Asus Eee ... using it right now,.
Run **lxrandr**, save/apply the resolution you like ... I think only 1024x600 is max using the built-in screen ... definitely NOT that number you have listed in the OP. If you have an external monitor connected, other resolutions will be displayed, but don't expect anything over 768p to work well at all.

May need to install it. Use
**sudo apt-get install lxrandr**

If you don't want the bloat of the GUI, use xrandr. I didn't have any other dependencies under LXDE.

---

### Post by BADGER.BRAD on 2013-11-10
Thanks Thefu,

I did as you said and found this was already installed as it was what I was already using it only gives me one option 800x600 but running it from terminal gives me little more info (failed to get size of gamma for output default) my own note book and desktop PC using Lubuntu from the same disk allow me many different resolutions.

Thanks again

---

### Post by TheFu on 2013-11-10
Does **xrandr** agree with the lxrandr resolutions? I think they get the info from the same place.

Do you know the specific resolutions supported by the display? If so, you could add a monitor section to the /etc/X11/xorg.conf file (probably need to create it) with the other supported modes. Clearly, only supported modes should be put in that file, otherwise ... it could be bad.  LCDs won't have "catastrophic failures" like the old CRTs did (burning smell and NEVER working again), but ... make certain you can ssh in from a different machine to remove the xorg.conf file if your tweaks totally screw over the display.
**man xorg.conf** to learn more.

BTW - here's mine:```
~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+   65.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
```

I've used this netbook as an XBMC server connected to a TV.  1024x768 was the resolution there. The CPU was unable to playback any videos over 600p thanks to non-existent GPU support. Any higher resolutions would stutter.

---

### Post by BADGER.BRAD on 2013-11-10
both agree with each other giving only one screen res 800x600 I'm going to try and reinstall Lubuntu in the hope that it loaded incorrectly.

---

### Post by TheFu on 2013-11-10
I doubt that will help.  You just need to get X to understand the GPU and Monitor settings.
It could be a hardware issue - check the log files especially the X.log.0

---

### Post by BADGER.BRAD on 2013-11-16
Hello again Thefu,

I have tried various flavours of linux on the Eee Pc all have the same problem (only 800x600 screen res available) so looks as if it is a linux problem.Have you any idea how I go about getting it to work correctly ? I tried Ubuntu but found I could not close any windows as the quit button was off screen. If you can help please give me step by step instructions as I'm a relative novice with the workings of linux.Not sure if there is any connection but I have an error message showing  which reads the error message was broken count <0 

Thanks

---

