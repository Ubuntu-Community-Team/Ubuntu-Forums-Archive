---
title: "Login screen was resized after upgrade?"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by svriderpokey on 2008-04-26
Login screen was resized after upgrade?  Now I can't see all of it.  How do I manually adjust resolution of the login screen?

---

### Post by lemming465 on 2008-04-26
I've got this problem too after upgrading from gutsy.  Once I log in the gnome desktop resolution is OK, and if we switch users, the second login is also offscreen, but bopping back and forth brings up normal unlock dialogs.  So I'm guessing the problem is somewhere in gdm, but I haven't investigated it yet.  Alpha 6 didn't do this.  It doesn't happen on my laptop (ati video); it does happen on an aging desktop ("nv" driver).

---

### Post by gatownsend on 2008-04-26
Same problem here after upgrading from gutsy.  I also have an Nvidia graphics card.  Tried it with and without the NV driver with the same result.   It appears to me that the login screen is exactly 4 times larger than it should be, so I'm only seeing about 25% of it (i.e. it twice as wide and twice as high as it should be).  I end up seeing the upper left quarter of it.

~Gary

---

### Post by mocha on 2008-04-26
Same here. Upgrade from Gutsy, Nvidia card.

---

### Post by bsell on 2008-04-26
I have an Nvidia card and had problems too. I had to edit the xorg.conf file to adjust the login screen resolution after backing up the file, of course.

```
sudo gedit /etc/X11/xorg.conf
```Change the resolution in the Display subsection.

---

### Post by mocha on 2008-04-26
heh.  I just did a similar thing to fix it:

```
Modes      "1152x864@75" "1024x768" "800x600"
```

Now my login screen and desktop are they way I want them, 1152x864 at 75 Hz

---

### Post by gatownsend on 2008-04-27
Searched around here, and this is what I had to do to get it working the way I wanted.  I had to change the "virtual" setting from 2048 x 1536 to 1280 x 1024, as noted above by bsell.  I also had to change the "modes" listing so that the 1280 x 1024 setting was the first in the list.  This got it so that  everything was 1280 x 1024 for me.

I know in gutsy all I did was select my screen resolution in preferences and click a box that said something like "apply to all" or something.  I couldn't find that option in hardy and this was the only thing that would get it displaying correctly for me.

~Gary

---

### Post by svriderpokey on 2008-04-29
bsell, you are the man today... and all day tomorrow too.

---

