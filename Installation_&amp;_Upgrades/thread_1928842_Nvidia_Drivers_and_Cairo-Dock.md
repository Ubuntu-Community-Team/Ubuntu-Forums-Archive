---
title: "Nvidia Drivers and Cairo-Dock"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by Bobhuber on 2012-02-20
The latest Nvidia drivers (295.20) cause cairo-dock to crash when attempting to use open GL with the dock. Any one else having this problem ? Report it to the folks at CD   [http://www.glx-dock.org/bg_forumlist.php](http://www.glx-dock.org/bg_forumlist.php).

---

### Post by LewisTM on 2012-02-21
+1
It seems to be a bug with a post-release NVIDIA driver update.
Reverting to the current recommended driver in the Additional Drivers app will solve the problem.

---

### Post by Bobhuber on 2012-02-21
> **LewisTM said:**
> +1
It seems to be a bug with a post-release NVIDIA driver update.
Reverting to the current recommended driver in the Additional Drivers app will solve the problem.
It's not post release. That's the most recent  certified release just posted on Nvidia's site. So unless the wizards at ubuntu and x-org do some fancy talking to Nvidia we will be stuck with the older drivers untill Nvidia or Cairo-Dock decide to do something about it. The post-release 295-17 drivers did the same thing (reported to the folks at CD at the time) so I'm not holding my breath. It's not really a problem but the new drivers seem to speed things up a bit.

---

### Post by Morozov on 2012-02-21
Have you try to install new 3.2 kernel? I handle Nvidia driver better. Best should be with 12.04 arrival, video card I have GeForce 9400M handled easy (no crashes)

---

### Post by Bobhuber on 2012-02-21
> **Morozov said:**
> Have you try to install new 3.2 kernel? I handle Nvidia driver better. Best should be with 12.04 arrival, video card I have GeForce 9400M handled easy (no crashes)
I'm running 3.3rc4 Kernel that I compile myself and I install Nvidia using there proprietary  drivers and run file. I'm also using the BZR version of Cairo-Dock which may make a difference although I doubt it looking at the posts on there site. Are you running Cairo-Dock with the new drivers ??

---

