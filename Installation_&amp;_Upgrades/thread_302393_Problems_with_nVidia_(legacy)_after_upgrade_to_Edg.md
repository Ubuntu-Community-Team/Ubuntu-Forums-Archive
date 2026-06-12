---
title: "Problems with nVidia (legacy) after upgrade to Edgy"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by redgum on 2006-11-18
Hi - following an upgrade to edgy today, I'm now getting the following GLX errors...

Xlib:  extension "GLX" missing on display ":0.0".

I'm running the following card:

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

has anyone come across this & fix??

redgum

---

### Post by redgum on 2006-11-18
Fixed it...

added to the bottom of /etc/X11/xorg.conf :

      Section "Extensions" 
              Option  "Composite" "Disable"
      EndSection


restarted X & it worked.

Link with info...

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

