---
title: "Display Settings not being set (9.10) (Dual Monitors)"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sp0tteh on 2009-10-17
Hey all, thought i would give the beta a shot and i must say it's looking good.

though it didn't take long to come across an issue :(.

Anyway,

When i setup my display settings (Dual Desktop) using System -> Preferences -> Display, it asks me to log off and log back in, but when i do the settings a set aren't applied. Still shows as default (Mirror Screens).

However if i unplug the second monitor and just change the res on one, it works fine.

Any ideas?


lshw -C Display | grep product:

M56P [Radeon Mobility X1600]


sp0tteh@ejofr4wrtw:~$ cat /etc/X11/xorg.conf

Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
        SubSection "Display"
                Virtual 2048 2048
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

---

### Post by jaogihao on 2009-10-17
Well I just installed Ubuntu today and ran into a somewhat similar problem.  I have my LCD tv as a second display.  I went into the dispay options and set each monitor to the highest resolution option for both (the laptop at 16:9 and the tv at 4:3).  But when i tried to move firefox to the second display it would hit an "invisible" wall and would not let me move the browser all the way into the second display.  so i changed the second display to the next highest resolution but in 4:3 format and this fixed the problem.  Maybe this would help you?  If not, i'm sorry.  It's my first day after all! :P

---

### Post by Longinus00 on 2009-10-17
> **Sp0tteh said:**
> Hey all, thought i would give the beta a shot and i must say it's looking good.

though it didn't take long to come across an issue :(.

Anyway,

When i setup my display settings (Dual Desktop) using System -> Preferences -> Display, it asks me to log off and log back in, but when i do the settings a set aren't applied. Still shows as default (Mirror Screens).

However if i unplug the second monitor and just change the res on one, it works fine.

Any ideas?


lshw -C Display | grep product:

M56P [Radeon Mobility X1600]


sp0tteh@ejofr4wrtw:~$ cat /etc/X11/xorg.conf

Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
        SubSection "Display"
                Virtual 2048 2048
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

There is currently a bug which makes it so display properties isn't correctly updating your xorg.conf file. I don't have the bug # offhand but I'll find it and edit it in later. In the meantime, to fix your problem change the following and you should be able to enable multiple desktops again.

```
Virtual 4096 4096
```

*Well the bugreport said this was fixed, I haven't tested it yet. Are you up to date on your packages?

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/433856](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/433856)

---

### Post by Sp0tteh on 2009-10-17
> **Longinus00 said:**
> There is currently a bug which makes it so display properties isn't correctly updating your xorg.conf file. I don't have the bug # offhand but I'll find it and edit it in later. In the meantime, to fix your problem change the following and you should be able to enable multiple desktops again.

```
Virtual 4096 4096
```

*Well the bugreport said this was fixed, I haven't tested it yet. Are you up to date on your packages?

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/433856](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/433856)

Thanks, this is the issue i am seeing.

I have the update manager set to receive latest updates, but it appears this one isn't appearing.

sp0tteh@ejofr4wrtw:~$ dpkg -s screen-resolution-extra
Package: screen-resolution-extra
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 184
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
**Version: 0.10**


"This bug was fixed in the package screen-resolution-extra - 0.11"


*Edit

I had my source set to a local file mirror, change it to the main server and i am now seeing 257mb of updates available. So looks like the mirror i was using isn't up to date.

**Edit

Confirmed, Working with latest  screen-resolution-extra:

sp0tteh@ejofr4wrtw:~$ dpkg -s screen-resolution-extra
Package: screen-resolution-extra
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 184
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
**Version: 0.11**


Thanks again for the help.

---

