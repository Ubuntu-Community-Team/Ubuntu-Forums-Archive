---
title: "Disable VGA port on most video cards"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by vociferous666 on 2010-12-19
Referring to old thread:
[http://ubuntuforums.org/showthread.php?t=701588](http://ubuntuforums.org/showthread.php?t=701588)

Background:  
I have a mobo with IGP. has VGA and HDMI ports on it. 
it is hooked up to my lcd tv in the living room via HDMI. 
when the tv is on another input, the video card will not detect the tv on boot 
and automatically switch to VGA port. 
so when i VNC in, resolution has been set to 4000x4000!!
since i would like to use HDMI as default, i disabled VGA completely and have had no problems.

in the section Monitor in your /etc/X11/xorg.conf

```
Section "Monitor"
Identifier "VGAConnection"
Option "Disable" "true"
EndSection
```

make sure u use "true" and not "True"

the case matters and someone posted the incorrect syntax.
for new users this is a headache.
plz keep this in mind before giving advice to newbies ;)

---

