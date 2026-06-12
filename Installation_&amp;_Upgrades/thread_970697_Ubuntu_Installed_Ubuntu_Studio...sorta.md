---
title: "Ubuntu Installed Ubuntu Studio...sorta"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by Mohamedzv2 on 2008-11-04
I used the command terminal and typed in "sudo apt-get install ^ubuntustudio-desktop" and I got just about everything from ubuntu studio...with the exception of the multimedia apps. So what should I do to get them? Or do I have to install each one alone?

---

### Post by steveydoteu on 2008-11-04
> **Mohamedzv2 said:**
> I used the command terminal and typed in "sudo apt-get install ^ubuntustudio-desktop" and I got just about everything from ubuntu studio...with the exception of the multimedia apps. So what should I do to get them? Or do I have to install each one alone?

Typing in the following and giving a double tab:

```
sudo apt-get install ubuntustudio-
```

Gave me the following options:

```
ubuntustudio-artwork           ubuntustudio-icon-theme
ubuntustudio-audio             ubuntustudio-look
ubuntustudio-audio-plugins     ubuntustudio-menu
ubuntustudio-controls          ubuntustudio-screensaver
ubuntustudio-default-settings  ubuntustudio-sounds
ubuntustudio-desktop           ubuntustudio-theme
ubuntustudio-gdm-theme         ubuntustudio-video
ubuntustudio-graphics          ubuntustudio-wallpapers
```

I imagine audio, video and maybe graphics are the ones you require, although it could be more beneficial only installing what applications you want: [https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)

---

### Post by snowpine on 2008-11-04
Unlike, for example, ubuntu-desktop or xubuntu-desktop, ubuntustudio-desktop does not contain the apps. :)

ubuntustudio-audio will give you the audio apps, ubuntustudio-video will give you the video apps, etc.

---

