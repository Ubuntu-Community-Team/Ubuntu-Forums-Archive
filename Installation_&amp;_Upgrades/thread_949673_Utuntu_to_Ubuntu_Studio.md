---
title: "Utuntu to Ubuntu Studio"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by pisio on 2008-10-16
How I can update/upgrade  my OS to Ubuntu Studio ?

---

### Post by snowpine on 2008-10-16
Here you go:
[http://ubuntuforums.org/showthread.php?t=900676](http://ubuntuforums.org/showthread.php?t=900676)

---

### Post by ace214 on 2008-10-16
If you go into the Synaptic Package Manager and search for "ubuntustudio" you will see the packages that it installs. Some of these are metapackages that will install a bunch of programs (which is probably what you want). There is a metapackage for audio, audio plugins, video, and graphics. The other packages are for the artwork. If you truly want to have a UbuntuStudio system, it would be better to just reinstall.

---

### Post by forger on 2008-10-16
```
sudo aptitude install ubuntustudio-desktop
```

---

### Post by ace214 on 2008-10-16
> **forger said:**
> ```
sudo aptitude install ubuntustudio-desktop
```

That doesn't install the application metapackages.

If you want to know what each package installs look in Synaptic or here: [http://packages.ubuntu.com/search?keywords=ubuntustudio&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=ubuntustudio&searchon=names&suite=hardy&section=all)

---

### Post by forger on 2008-10-16
oops, sorry, you're right :)

> ubuntustudio-audio - Ubuntu Studio Audio Package
ubuntustudio-audio-plugins - Ubuntu Studio audio plugins Package
ubuntustudio-controls - Ubuntu Studio Controls is a small app that changes A/V settings.
ubuntustudio-default-settings - Default settings and artwork for the Ubuntu Studio desktop
ubuntustudio-desktop - Ubuntu Studio Desktop Package
ubuntustudio-gdm-theme - Ubuntu Studio - GDM theme
ubuntustudio-graphics - Ubuntu Studio graphics Package
ubuntustudio-icon-theme - Ubuntu Studio Icon theme
ubuntustudio-look - Ubuntu Studio look
ubuntustudio-menu - Menu for Ubuntu Studio
ubuntustudio-screensaver - Ubuntu Studio screensaver
ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
ubuntustudio-video - Ubuntu Studio video Package
ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
usplash-theme-ubuntustudio - Usplash theme for Ubuntu Studio

---

### Post by snowpine on 2008-10-16
Yes, it is neat the way they set it up so you can, for example, install only the video apps if you don't work with audio. :)

---

### Post by pisio on 2008-10-16
> **snowpine said:**
> Here you go:
[http://ubuntuforums.org/showthread.php?t=900676](http://ubuntuforums.org/showthread.php?t=900676)

10x,
but programs in studio edition can't  convert avi + subs in AVI

---

