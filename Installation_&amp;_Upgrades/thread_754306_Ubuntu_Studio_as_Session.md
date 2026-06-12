---
title: "Ubuntu Studio as Session?"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by stringkarma on 2008-04-13
In the past I have had ubuntu and kubuntu on the same computer and I can change the session from the login screen.

I thought that I could do this with ubuntu studio and ubuntu, however when I try 

```
:~$ sudo apt-get install -s ubuntustudio-desktop
[sudo] password for joel:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apmd gtk2-engines-murrine scim-modules-table scim-tables-additional
  tango-icon-theme tango-icon-theme-common totem totem-gstreamer totem-mozilla
  ubuntustudio-default-settings ubuntustudio-gdm-theme ubuntustudio-icon-theme
  ubuntustudio-look ubuntustudio-menu ubuntustudio-screensaver
  ubuntustudio-sounds ubuntustudio-theme ubuntustudio-wallpapers
  usplash-theme-ubuntustudio
Suggested packages:
  xapm kdelibs-data
The following packages will be REMOVED:
  ubuntu-desktop ubuntu-sounds
```

I can see that it wants to remove ubuntu-desktop. Can I not have both? I'm not willing to risk it unless I know that I can go back.
Thanks

---

### Post by forestpixie on 2008-04-13
I'm guessing that ubuntu-sounds is part of ubuntu-desktop - as ubuntu-desktop is a metapackage with ubuntu-sounds gone so has the metapackage - but it doesn't mean you've lost ubuntu.

I had both shortly before I went to hardy

---

