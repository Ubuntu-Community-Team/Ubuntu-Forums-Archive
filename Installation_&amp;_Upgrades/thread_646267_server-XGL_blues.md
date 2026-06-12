---
title: "server-XGL blues"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by wescrow on 2007-12-21
When I enable server-XGL my system lags badly and many icons are distorted with little black bars.  Any idea what this could be?

Everything runs fine with XGL disabled, but I think I must need it enabled to use desktop effects.

My DVD playback doesn't work either no matter how many walk-thrus and how-tos I go through.  i have an ATI Xpress 200.

---

### Post by eternicode on 2007-12-21
XGL has incompatibilities with Intel chipsets, so if you're using Intel video drivers (for example, i810), XGL will seem to bog your system, and the eyecandy will become an eyesore.  I have compiz setup on Kubuntu Feisty without enabling XGL, and it works smooth as silk.  Of course, I also tweaked it to death, but enabling XGL makes it act slow either way.

As for DVDs, I had the same problem, until I discovered I needed dvd-decoder packages.  Try installing libdvdcss2 (as mentioned [_at LifeHacker_]("http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php") -- it's not in any official repos, so you'll have to download a .deb file from [_VideoLAN_]("http://download.videolan.org/pub/libdvdcss/") (go to the latest version number, then to "deb" directory, download the package that DOESN'T have "dev" in the name) and install it from that file.


Edit:
ATI ... is that the video card?  I'm not sure about XGL incompatibilities with ATI chipsets...at any rate, try compiz ("desktop effects" under gutsy, I guess) without XGL and see if it works well.

Edit2:
Might check your video driver against the list at [_Gentoo Wiki_]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL").  You should be able to find the driver name in your /etc/X11/xorg.conf file.  I couldn't figure out how my i810 drivers fit in under the Intel section, but you may be able to make better sense of it. ;)

---

### Post by wescrow on 2007-12-21
> **eternicode said:**
> XGL has incompatibilities with Intel chipsets, so if you're using Intel video drivers (for example, i810), XGL will seem to bog your system, and the eyecandy will become an eyesore.  I have compiz setup on Kubuntu Feisty without enabling XGL, and it works smooth as silk.  Of course, I also tweaked it to death, but enabling XGL makes it act slow either way.

Interesting.  I will have to google this some more.

> **eternicode said:**
> 
As for DVDs, I had the same problem, until I discovered I needed dvd-decoder packages.  Try installing libdvdcss2 (as mentioned [_at LifeHacker_]("http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php") -- it's not in any official repos, so you'll have to download a .deb file from [_VideoLAN_]("http://download.videolan.org/pub/libdvdcss/") (go to the latest version number, then to "deb" directory, download the package that DOESN'T have "dev" in the name) and install it from that file.


I have already attempted this.  I actually used the lifehacker guide.  I can rip DVDs which tells me the restricted codecs are working, but my DVD playback is not working still.  

> **eternicode said:**
> 
Edit:
ATI ... is that the video card?  I'm not sure about XGL incompatibilities with ATI chipsets...at any rate, try compiz ("desktop effects" under gutsy, I guess) without XGL and see if it works well.


Yes the video card is an ATI Radeon Xpress 200.   I don't know if it is working fine or not.  What I've read states that if the video card is not working the processor will act in its stead.  It seems to run well enough without XGL enabled, but it still isn't as fast as it is on my laptop which has a Intel Celeron M 1.3 GHz (Desktop has Intel Celeron D 3.2 GHz),  1.256 GB RAM (Desktop has 1.512 GB RAM), and an older version ATI Radeon video card than my desktop.  Plus my laptop has DVD playback.

> **eternicode said:**
> 
Edit2:
Might check your video driver against the list at [_Gentoo Wiki_]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL").  You should be able to find the driver name in your /etc/X11/xorg.conf file.  I couldn't figure out how my i810 drivers fit in under the Intel section, but you may be able to make better sense of it. ;)
[/QUOTE]

I'll be sure to give this a try.

---

