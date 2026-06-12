---
title: "Ubuntu Studio install through Windows?"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by coldbluesteel on 2008-08-16
I would like to install Ubuntu Studio 8.04 for my wife to try. She uses Windows products currently for video development.

I am wondering if all Ubuntu 8.04 based distros will allow installation through Windows? Or just the base Ubuntu? Because my copy of Ubuntu Studio doesn't seem to let me. Am I missing something?

The reason I would like to do it this way is since she's not Linux convert (yet) I'd like to keep her Windows bootloader in tact, in case she decided not to use Ubuntu Studio.

Thanks,

CBS

---

### Post by Elfy on 2008-08-16
I'm not sure if there is a wubi for studio, which is what you are talking about - don't think so.

If I wanted to do that within windows I would install a default ubuntu with wubi, once it had been installed I would install ubuntustudio through the terminal. This is the command to do so from a terminal

```
sudo aptitude install ubuntustudio-desktop
```

You could install seperate parts if you wished afaik - replace ubuntustudio-desktop

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

---

### Post by coldbluesteel on 2008-08-16
I'm loading Ubuntu 8.04 with wubi now, if I update to Ubuntu Studio, would I still be able to run the uninstaller through Windows should she choose to? 

CBS

---

### Post by logos34 on 2008-08-16
more info:
[https://help.ubuntu.com/community/UbuntuStudio/](https://help.ubuntu.com/community/UbuntuStudio/)
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy)

If you want to run the linux-rt kernel in addition for better performance:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
(-->'Real Time Kernel & Xruns' & 'Real-Time Support')

---

### Post by coldbluesteel on 2008-08-16
I have Ubuntu up and running, loaded through wubi. Compix installed, WINE installed.

But my big question is, if I upgrade/change to Ubuntu Studio and she doesn't like it, will I still be able to uninstall through Windows? She's digging the Compiz desktop and using the distro so far (she's played on my laptop for a bit) but if the video editing software doesn't meet her needs she won't want 2 OSes on her machine.


CBS

---

### Post by Elfy on 2008-08-16
afaik you should still be able to do so - you will in fact now have 2 ubuntu that you can use - change them at the login window.

As I understand wubi installs on a virtual partition, if you want to uninstall it througgh Add/Remove it removes the partition and all thats on it, even if it doesn't I don't think it is too much trouble to get rid of.

This is the wubi wiki - it might be worth a look at

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by coldbluesteel on 2008-08-16
Woo hoo it works!!

Wife is happy and we both say THANKS!

CBS

---

### Post by Elfy on 2008-08-16
cool - can you mark thread solved please

---

### Post by coldbluesteel on 2008-08-16
I hope I did this right?

Thanks again!

CBS

---

### Post by steveneddy on 2008-08-16
WUBI is horrible!

Just partition and install it so you can get the actual experience.

You may as well just run it off of the Live CD than use WUBI.

The GRUB boot menu will show the Windows partition, and when she gets tires of it, just run
```

fixmbr

```
from Windows.

Easy.

---

