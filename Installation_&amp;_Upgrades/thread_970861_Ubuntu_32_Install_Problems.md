---
title: "Ubuntu 32 Install Problems"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by Lex-Man on 2008-11-04
I have installed the Ubuntu 32-bit edition on my machine using Wubi.  But when I boot Ubuntu loads and then drops into a black screen where my monitor complains that there is no input and goes into stand by mode.

I have tried loading as a live CD and the same thing happens.

Is it worth downloading the ISO again how can I tell if the file is corrupt?

---

### Post by taurus on 2008-11-04
I don't think the burnt is corrupted.  It's more like a problem with the X server.  See if you can boot into recovery mode and reconfigure your X server again with

```
dpkg-reconfigure xserver-xorg
shutdown -r now
```

---

### Post by milaz on 2008-11-04
Please, see also these topics:

[http://ubuntuforums.org/showthread.php?t=966337](http://ubuntuforums.org/showthread.php?t=966337)
[http://ubuntuforums.org/showthread.php?t=965237](http://ubuntuforums.org/showthread.php?t=965237)

and, most notably,

[http://ubuntuforums.org/showthread.php?t=963425](http://ubuntuforums.org/showthread.php?t=963425)

It looks like the screen goes blank by more than three different reasons, and there are some solutions found, unfortunately, not for the problem I have with blank screen :(

---

