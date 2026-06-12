---
title: "[SOLVED] Ibex Issues: AWN and Nvidia Issues"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by anxiousdog on 2008-10-30
So I did the upgrade and some things went awry, but I'm back on track now except two things.

First, AWN Manager was uninstalled during the upgrade. I tried reinstalling it, but things are all wonky. Certain applets disappeared, open tasks won't show up on the bar, etc. I'm not as worried about this as the other issue, but I wanted to document it and see if anyone has a quick fix for this.

My second and largest issue s that my Nvidia X Server settings was also uninstalled. I reinstalled it and set up my dual monitors and clicked "Save configuration file". The Nvidia window closed and when I reboot or reload GRUB, things go back to the original settings.

I did run ```
sudo nvidia-settings
```

The window opens but I get a string of errors like: 

```
ERROR: Unable to assign attribute CursorShadow specified on line 30 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 31 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 32 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 33 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 34 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 35 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 36 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 37 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 38 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 39 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 40 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 41 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 42 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 43 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 44 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 45 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 46 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 47 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 48 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       49 of configuration file '/home/anxiousdog/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       50 of configuration file '/home/anxiousdog/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 51 of
       configuration file '/home/anxiousdog/.nvidia-settings-rc' (no Display
       connection).

```

The settings window opens, but I still can't save any changes. Any help here?

---

### Post by anxiousdog on 2008-10-30
> **anxiousdog said:**
> So I did the upgrade and some things went awry, but I'm back on track now except two things.

First, AWN Manager was uninstalled during the upgrade. I tried reinstalling it, but things are all wonky. Certain applets disappeared, open tasks won't show up on the bar, etc. I'm not as worried about this as the other issue, but I wanted to document it and see if anyone has a quick fix for this.


Okay I've had some odd things happen with AWN and there always seems to be a different fix. I found [this post that solved my problem with AWN]("http://ubuntuforums.org/showpost.php?p=4377048&postcount=6"). 

Now on to the Nvidia issues...

---

### Post by anxiousdog on 2008-10-31
Not sure what I did, but something fixed it. I think it may have been [this thread]("http://ubuntuforums.org/showthread.php?t=652382") and this command:

```
gksudo nvidia-settings
```

---

