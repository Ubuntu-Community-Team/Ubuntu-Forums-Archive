---
title: "Nouveau: visual effects and monitor refresh rate problem"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Rackstar on 2010-03-11
Hi,

I was very curious about the Nouveau driver, so I thought I'd give it a try on this up-to-date Lucid laptop.

I disabled the NVidia driver and rebooted.

Two things that I notice:
1) Program "monitors" is unable to identify the refresh rate of my second monitor (has to be 65Hz, and I am only able to choose between 60 en 75). But I like the program "monitors" much more than the NVidia app.
2) I'm not able to enable visual effects, not even to "normal", without being asked to install the NVidia drivers. I though this was possible with Nouveau (wasn't sure about "extra"). Is this normal?

Thanks!

---

### Post by Melcar on 2010-03-11
Nouveau does not have 3D, I don't think.  It's mostly UMS/KMS modesetting and 2D acceleration.  You will still need the binary drivers for 3D.  In the future you will start seeing 3D support with nouveau, just not now.

---

### Post by tad1073 on 2010-03-11
[http://ubuntuforums.org/showthread.php?t=1406126](http://ubuntuforums.org/showthread.php?t=1406126)
[http://ubuntuforums.org/showthread.php?t=1416185&highlight=nouveau](http://ubuntuforums.org/showthread.php?t=1416185&highlight=nouveau)

---

### Post by Rackstar on 2010-03-11
Also, I have no plymouth and screen-resolution at GDM is way off for both screens, after GDM it's ok.

I didn't realize that 3D-capabilities were necessary for visual effects to "normal", now it's none? Can someone confirm this?

Really great now, is that wallpapers aren't stretched over both screens, but both screens have their wallpaper.

---

### Post by Rackstar on 2010-03-11
Oh, ok, thanks for the links!

I already took a quick look there, but I overread that gnomeuser was using xorg-edgers ppa.

---

