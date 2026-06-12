---
title: "I messed up the resolution"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by pepsifx357 on 2008-03-08
I messed up the resolution in my installation, is there a safe mode I can get to? because I can't log in becuase the video is to messed up to log in.  It just keeps trying to get to the login screen and starts over, when I use the live cd it works but I can't change the resolution in my installed ubuntu.  How do I fix this?

---

### Post by taurus on 2008-03-08
Boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

