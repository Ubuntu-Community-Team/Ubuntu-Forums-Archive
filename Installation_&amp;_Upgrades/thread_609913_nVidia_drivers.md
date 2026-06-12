---
title: "nVidia drivers"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by pcostanza on 2007-11-11
Sorry for such a dumb question but just how do I tell if I have the nVidia drivers enabled?

---

### Post by don_crissti on 2007-11-11
AFAIK... open /etc/X11/xorg.conf after Section "Monitor" you should have something like this:
Section "Device"
    Identifier "device1"
    VendorName "nVidia Corp."
    BoardName "NVIDIA GeForce 7 Series"
    [COLOR="black"]Driver "nvidia"[/COLOR]
    Option "DPMS"
EndSection

So your driver has to be "nvidia"
if instead "nvidia" you have "nv" you haven't enabled your driver

---

### Post by pcostanza on 2007-11-11
Thanks, mine does say nvidia and shows the correct vid card.  I was just hoping to be able to get a bit 'cleaner' screen.  Seems that my colors are dull and I I can't adjust my refresh rate.  I only have a choice of 50hz at 1024 x 768.  I would like change the res to something higher.  Guess I may have to live with this setup for now.

---

### Post by Dragons World on 2007-11-15
Have you loaded the restricted drivers? I had same problem and went to Applications/add remove/restricted drivers manager. Check it and install the program.

---

### Post by pcostanza on 2007-11-15
> **Dragons World said:**
> Have you loaded the restricted drivers? I had same problem and went to Applications/add remove/restricted drivers manager. Check it and install the program.

I did have it installed but just removed it.  Are you saying I should reinstall the Restricted Manager again?

---

### Post by Dragons World on 2007-11-15
I have an Nvidia FX 5200 card and the refresh rate was so low that the screen was flickering so badly that it almost gave me seizers. I enabled the Restricted Drivers and also enabled the Nvidia Binary X.org driver ('new' driver) and the flickering went away. I adjusted the screen to 1024 x 768. Don't bother with the resolution if your happy with the way it looks. I tried to adjust the resolution past 50hz and the restricted drivers were disengaged and I ended up with a mess on my hands and back to a flickering screen. But this is what worked for me.

---

### Post by Dragons World on 2007-11-15
Check this  link out and see if it helps any.

[http://www.neowin.net/forum/lofiversion/index.php/t595237.html](http://www.neowin.net/forum/lofiversion/index.php/t595237.html)

---

### Post by pcostanza on 2007-11-15
Thanks, I'm reading my **** off trying to suck up all the info.

---

### Post by Dragons World on 2007-11-15
I'm still reading. I don't think the process ever ends but I hear it gets better.  After awhile when you understand where most of the stuff is located in the linux program it gets easier. It's difficult so don't give up. Good Hunting.

---

### Post by MightyMe on 2007-11-16
You can also try and type "nvidia-settings" at the command prompt. This will give you a better GUI front to the graphics card and you can check all settings there. I cant understand why it's not visible in the menus after having enabled the restricted device driver, but that's another matter.

---

### Post by froy02 on 2007-11-16
The most cause for not getting the resolution of your screen is because you have the wrong monitor selected.  Go to Systems > Administration > then click on  Screen and Graphics.  Check if your monitor is the one selected and if not select it and you should be able to set the refresh rate that your MONITOR is capable of displaying.

You might have to re-start the computer to take effect.

---

### Post by Dragons World on 2007-11-26
[http://ubuntu-tutorials.com/2007/10/26/restricted-drivers-manager-vs-envy/](http://ubuntu-tutorials.com/2007/10/26/restricted-drivers-manager-vs-envy/)

Check out this thread. I've used this (ENVY) before in others distros including this one vice the restricted drivers and it works great.

---

