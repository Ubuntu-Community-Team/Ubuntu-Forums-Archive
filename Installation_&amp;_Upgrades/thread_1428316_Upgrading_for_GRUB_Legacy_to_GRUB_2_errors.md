---
title: "Upgrading for GRUB Legacy to GRUB 2 errors"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by ShadowsOfSilver on 2010-03-12
Nevermind, I already have GRUB2

---

### Post by MichealH on 2010-03-12
How 'bout reading this ?
[http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html)

If you would like to beautify it see my thread here:

[http://ubuntuforums.org/showthread.php?t=1425075](http://ubuntuforums.org/showthread.php?t=1425075)

---

### Post by ShadowsOfSilver on 2010-03-12
Would the first one work for Karmic?

---

### Post by MichealH on 2010-03-12
It said for Ubuntu Jaunty and Karmic

---

### Post by ShadowsOfSilver on 2010-03-12
I didn't see that before. ^^;

I tried that and I got 

```
ubuntu@ubuntu:~$ sudo apt-get install grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-pc
E: Package grub2 has no installation candidate

```

---

### Post by MichealH on 2010-03-12
I just remembered... grub-pc is grub2 in the Karmic Repos. So If you probably purge it then install it?

---

### Post by ShadowsOfSilver on 2010-03-12
Nevermind, I apparently already have grub 2

---

