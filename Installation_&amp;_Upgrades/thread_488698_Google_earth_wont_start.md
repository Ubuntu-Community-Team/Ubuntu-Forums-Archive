---
title: "Google earth wont start"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by asnd16 on 2007-06-30
Google Earth Gets stuck at the Initializing screen, I think this has something to do with the fact that I am also unable to run desktop Effects.  Please help. . .
Error>  sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.1.7076.4458..........................................................................
Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
Xlib:  extension "XFree86-DRI" missing on display ":0.0".


Thanx.

---

### Post by Bandude231 on 2007-12-08
I have the same issue.  But I am able to use desktop effects.   So you could rule that theory out.  Unfortunately I don't know enough to fix your problem but this may help someone diagnosis it. 

Thanks

---

### Post by jespdj on 2007-12-08
This most likely has something to do with your graphics card. What brand and model is your graphics card? Does it support accelerated 3D graphics? What video driver are you using? Not all Linux video drivers support 3D graphics (properly), even if the graphics card has the capabilities.

nVidia should in general work fine, ATI video drivers are unfortunately still not really good.

p.s. Bandude231, why did you reply to a post from June 30th?

---

### Post by daitau on 2007-12-09
I amended ~/.gnome/apps/Google-googleearth.desktop according to

[http://triligon.org/triligon/blog/getting_google_earth_to_run_on_ubuntu_7_10_with_intel_gma_x3100_graphics](http://triligon.org/triligon/blog/getting_google_earth_to_run_on_ubuntu_7_10_with_intel_gma_x3100_graphics)

  so the Exec line read

Exec=LIBGL_ALWAYS_INDIRECT=1 /home/MYUSERNAME/google-earth/googleearth %f

  and now I can run Google Earth with Desktop Effect on.

  For the record I am using NVidia 5200.

  Hope it helps.

---

