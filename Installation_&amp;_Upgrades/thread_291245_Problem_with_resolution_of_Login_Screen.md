---
title: "Problem with resolution of Login Screen"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by BobBlum on 2006-11-02
I just upgraded from Dapper to Edgy (final version).   The login screen is now at a very low resolution and is too large to fit on the monitor screen.  I have to move the login screen to get to the "Options" menu or to center the input fields.  I've tried both themed greeter and plain text options.  It is a mess.  This should never be permitted to happen in a distribution like Ubuntu.  Any solutions?  Thank you in advance.

---

### Post by Footer on 2006-11-04
I have the exact same problem (using Kubuntu upgraded from Dapper to Edgy) but it didn't happen at first.  It happened after I messed with the Nvidia drivers and xorg.conf.

If someone knows a solution, I'd be ever so grateful.

Thanks!

---

### Post by zenon on 2006-11-11
I did not upgrade from Dapper to Edgy.  My login screen resolution used to be full screen and now I have to move the mouse cursor to bottom of the screen several times to scroll to the session manager.  I don't know why it changed or how to correct it.  If you found a solution please share it.
Thanks,
Zenon

---

### Post by Next.Step on 2006-12-02
same problem here....

---

### Post by Dave54 on 2006-12-16
First, open terminal and type
```
sudo gedit /etc/X11/xorg.conf
```
Scroll down until you find the "screen" section. Mine looks like this:
```
Section "Screen"
 Identifier "Default Screen"
 Device  "NVIDIA Corporation NV34 [GeForce FX 5200]"
 Monitor  "A90f+"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
EndSection
```
Note where it says "DefaultDepth 24". That means we're interested in this part:
```
 SubSection "Display"
  Depth  24
  Modes  "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
```
Finally, under modes, move the screen resolution you like best to the front of the list. It will be used as your default screen resolution when you log in.

Good luck.
-Dave

Edit: well, I thought this would work, but when I tried it, the screen zoomed in to what I set but the login area stayed big. Seems I only got half of it

---

