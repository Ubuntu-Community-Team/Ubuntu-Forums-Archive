---
title: "GUI freezes on startup"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by mskadu on 2007-11-19
Hi,

I am re-posting this problem after a long time. I've re-installed Ubuntu 7.10 after a format. The install went through fine. When the machine starts into GUI mode for the first time, it freezes. I don't see a login screen. :confused:

Any suggestions?

---

### Post by zvacet on 2007-11-19
Maybe it is just graphic  card.Boot in recovery mode and type

```
dpkg-reconfigure xserver-xorg
```

select **vesa** driver.After that you should have GUI and you can start looking for drivers for your card.

---

### Post by mskadu on 2007-11-19
Ok. thanks for that. Video driver's weren't a problem. I've had pre-7.10 installs running fine before. Perhaps I should have mentioned that.

I re-configured by xserver-xorg and after a couple of tries enabled the framebuffer thingy in the options (not sure what that does). That seems to have work and now I am able to login to my desktop. I can see the menu and all.

Once the desktop settles (in about 5 seconds), the screen freezes again. Anything further I can do to check what's hanging? :confused:

---

