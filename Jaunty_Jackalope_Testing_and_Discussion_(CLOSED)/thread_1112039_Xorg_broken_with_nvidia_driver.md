---
title: "Xorg broken with nvidia driver"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by David A Knight on 2009-03-31
After booting this morning, so picking up updates from yesterday xorg seems to be horribly broken for me when using the nvidia driver, focus doesn't seem to be followed and appears "stuck" at various times on differing windows.  Updates to xorg today haven't fixed anything.   Anyone else experiencing anything similar?

Note: switching to nv is not an option, although it doesn't suffer the problem, as dual screen setup for me just doesn't work right under that driver and xv performance drops through the floor.

---

### Post by thonuz on 2009-03-31
Yes I had this problem and tried reconfiguring xorg and reinstalling Nvidia. 
All I did was add a section for driver nvidia to xorg.conf and its fixed.

---

### Post by David A Knight on 2009-03-31
> **thonuz said:**
> Yes I had this problem and tried reconfiguring xorg and reinstalling Nvidia. 
All I did was add a section for driver nvidia to xorg.conf and its fixed.

Already tried a reinstall + already had the driver specified in xorg.conf, still broken.

---

### Post by David A Knight on 2009-03-31
> **David A Knight said:**
> Already tried a reinstall + already had the driver specified in xorg.conf, still broken.

Just wiped out my existing file and saved a new one off from nvidia-settings and things seem to be working ok now, will need to add in the extra bits I had to see if one of those caused the problem.

---

### Post by loomsen on 2009-03-31
> **David A Knight said:**
> will need to add in the extra bits I had

Pretty likely that those bits caused it. What did u have in it if u don't mind? 
Many options are still spooking through the internet here and there, tho most of them are obsolete and/or default anyway. I'd try any new driver with a basic xorg.conf first, and then, if I actually experience difficulties, hardcoding my settings one after another.

However, the output of 
```

cat /var/log/Xorg.0.log | grep '(EE)'

``` will ahow you which errors your xorg.conf creates, and

```
cat /var/log/Xorg.0.log | grep '(WW)'
```
will show warnings.

Guess this could be of some use while bugbustin.

---

### Post by David A Knight on 2009-03-31
> **loomsen said:**
> Pretty likely that those bits caused it. What did u have in it if u don't mind? 
Many options are still spooking through the internet here and there, tho most of them are obsolete and/or default anyway. I'd try any new driver with a basic xorg.conf first, and then, if I actually experience difficulties, hardcoding my settings one after another.
...
...
Guess this could be of some use while bugbustin.

I've attached my previous xorg.conf file.

---

### Post by loomsen on 2009-03-31
Oh well, no doubt u had some extra bits ^^ Do you remember which does exactly what? 

I'd recommend checking your xlog, and not hardcoding default values.

However, one thing I'd like to ask you.

> 
    Option         "UseEvents" "1"


Does this option effect your CPU load anyhow? With the recent kernel versions I get pretty high loads here n there, but it's more like peaks. I wonder if enabling it would stop them. Guess I'll try...

Thx for sharing.

---

### Post by David A Knight on 2009-03-31
> **loomsen said:**
> Oh well, no doubt u had some extra bits ^^ Do you remember which does exactly what? 

I'd recommend checking your xlog, and not hardcoding default values.

However, one thing I'd like to ask you.



Does this option effect your CPU load anyhow? With the recent kernel versions I get pretty high loads here n there, but it's more like peaks. I wonder if enabling it would stop them. Guess I'll try...

Thx for sharing.

I think my reason for UseEvents 0 was stability when trying to use compiz, which are what most of my options in my screen section are there for.  The options have just built up over time from before they were defaults.  Infact 0 is the default for UseEvents.  With it as 1 it should be kinder to the cpu.

Coolbits -  lets you access the overclocking (not that I use it) and disable vertical blank  interupts setting in nvidia-settings

OnDemandVBlankInterrupts - used for power savings, by default the driver will poll 60 times a second, or whatever your refresh rate is which isn't needed for 2D graphics.

NoLogo - don't show the nvidia logo on startup of X, although for some reason I have it as false instead of true there

AllowDDCCI - looks like I can remove this as its going from the driver at some point anyway, some way of the card talking to the monitor.

XvmcUsesTextures - not sure if gstreamer/xine even make use of xvmc but if they do this makes the video use textures instead of being an overlay.

My "Configured Mouse" is a setup, which no longer works correctly for a logitech mx1000 in conjunction with xbindkeys to get all the buttons working, mouse still works fine, I just don't get all the intended buttons.

Synaptics part is just to get my touchpad going, again not working right anymore something broke with scrolling, lots of posts/threads on that though.

TwinView stuff is my 2 screens + positioning of them.

---

### Post by loomsen on 2009-03-31
Mouse, Keyboard and similar Input devices aren't configured in your xorg.conf anymore.

Your log will show:

> 
docter[/opt/local-apt/binary] cat /var/log/Xorg.0.log | grep '(WW)' | grep mouse 
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
docter[/opt/local-apt/binary] 

You prlly can disable this by AllowEmptyInput off ServerFlag I guess.

Actually, your issues might have other reasons tho...

Would you mind posting output of:

```

 ls -alh `find /dev -name nvidiactl`

```

As you might know, one very nice thing about linux is, that devices are handled just like files and folders. Thus it's possible to grant/disallow hardware access for certain groups of users, just like read/write/execute permissions on files/folders.
So, you have to be in the group video if you want to have full access to your DRI (=direct rendering infrastructure) of your device.(at least if you're running defaults)

You can check the link in my sig back for a more detailed explanation. In the meanwhile nvidia changed defaults from 0600 to 0660, still you have to be a member of the group video tho.

---

