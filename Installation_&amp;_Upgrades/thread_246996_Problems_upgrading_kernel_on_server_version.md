---
title: "Problems upgrading kernel on server version"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by leighsharpe on 2006-08-30
Hi All,
 I have installed dapper drake server version, which by default does not install X, desktop etc.
I need to update the kernel to 2.6.17, as I want to use some of the features in the newest kernel.
Following this thread:
[http://www.ubuntuforums.org/showthread.php?t=217657]("http://www.ubuntuforums.org/showthread.php?t=217657")
I am having a few problems:
make xconfig fails, I have no X server.
make menuconfig fails, with a VERY long list of errors.
I tried apt-get install xserver-xorg, which installed X11, but that doesn't seem to be enough.
I'm currently doing an apt-get install ubuntu-desktop in the hope that this will solve all dependencies, but it seems a bit drastic.
I don't really want to have all the extra bloat like openoffice etc., just to upgrade a kernel.

---

### Post by GarlicFish on 2006-08-30
To use make menuconfig you will need ncurses installed.
```
apt-get install libncurses5-dev

```

---

