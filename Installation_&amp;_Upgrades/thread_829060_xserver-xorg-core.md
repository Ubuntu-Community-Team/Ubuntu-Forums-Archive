---
title: "xserver-xorg-core"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by ugteuser on 2008-06-14
xserver-xorg-core (2:1.3.0.0.dsfg-12ubuntu8.4) hosed my X.  After entering user and password, X restarts rather like hitting CTRL-ALT-BACKSPACE.

I have verified it isn't a user config issue by adding a temporary user and attempting login with him --same symptoms.

How do I revert to the working xserver-xorg-core I had before yesterday's update?

I'm running Ubuntu 7.10 AMD64.

---

### Post by ugteuser on 2008-06-14
from /var/log/apt, here is the update that broke X for me:
```
Log started: 2008-06-13  13:34:44
(Reading database ... 170188 files and directories currently installed.)
Preparing to replace openssl-blacklist 0.1-0ubuntu0.7.10.4 (using .../openssl-blacklist_0.3.3+0.4-0ubuntu0.7.10.1_all.deb) ...
Unpacking replacement openssl-blacklist ...
Preparing to replace xserver-xorg-core 2:1.3.0.0.dfsg-12ubuntu8.3 (using .../xserver-xorg-core_2%3a1.3.0.0.dfsg-12ubuntu8.4_amd64.deb) ...
Unpacking replacement xserver-xorg-core ...
Setting up openssl-blacklist (0.3.3+0.4-0ubuntu0.7.10.1) ...
Setting up xserver-xorg-core (2:1.3.0.0.dfsg-12ubuntu8.4) ...
Log ended: 2008-06-13  13:34:59

```

I tried: ```
sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8.3
```
but got:
E: Version '2:1.3.0.0.dfsg-12ubuntu8.3' for 'xserver-xorg-core' was not found

What do I need to type to use the [apparently] 8.3 version that was working yesterday?

---

### Post by avtolle on 2008-06-14
Just a thought; have you tried reinstallation of your video card driver? And, which graphics card do you have in your system?

---

### Post by ugteuser on 2008-06-14
Ok, the problem was that the update clobbered the symlink: ```
/usr/lib/xorg/modules/extensions/libglx.so
```

It's the same issue as this [one]("http://ubuntuforums.org/showpost.php?p=4161947&postcount=6") from January.

Reinstalling my NVIDIA drivers may solve it in a roundabout way.  Fixing the symlink is much more direct.  Why does this update clobber the GLX module symlink?  It caused lots of pain when it happened in January, and they did it again.

---

