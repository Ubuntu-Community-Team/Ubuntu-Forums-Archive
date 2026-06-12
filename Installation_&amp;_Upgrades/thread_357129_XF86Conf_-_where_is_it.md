---
title: "XF86Conf - where is it?"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by giosetti on 2007-02-09
I need to re-adjust my monitor, so I tune it with xvidtune which throws out the modelines to enter in the XF86Conf.

But where is the XF86Conf? I can't find it neither in /etc/X11 nor in /usr/X11R6/etc/X11 where it used to be in the previous distributions I had.

So I'm confused - where does  Ubuntu store the Xconfigurations? 

Where do I need to store the modelines found with xvidtune?

---

### Post by taurus on 2007-02-09
It's in /etc/X11/xorg.conf.

```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by giosetti on 2007-02-09
Thanks. 

When I enter the modelines in xorg.conf the settings will be loaded on X start right? 

One thing strikes me: I had to do screen settings as each user, so there must be a config file for each user in the relating /home folders. 

I dont want that to be used. I want the xorg.conf settings be used on the start of X for all users.

Will there be a conflict? I dont know Ubuntu so well, with my mandriva system there were no user-related X-settigns, thats why I ask.

---

