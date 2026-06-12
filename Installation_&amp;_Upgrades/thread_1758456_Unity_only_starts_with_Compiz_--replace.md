---
title: "Unity only starts with Compiz --replace"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by Xilmwa on 2011-05-14
I have a rather odd problem. Ubuntu 11.04 came installed with the nvidia 173 drivers, which I replaced with the current ones. Neither loaded Unity, so I downloaded Nvidia's 270.41.06 drivers from their website. Still no unity.

If I run compiz --replace, however, compiz works fine, and Unity loads, albeit extremely buggy, most likely because all of the gnome components are still running (e.g., if I click anywhere on the top panel, it goes away).

Any ideas what could be causing this?

---

### Post by Linux_junkie on 2011-05-14
Best going to launchpad and report the bug if no one else has reported it.

---

### Post by Xilmwa on 2011-05-14
One more thing:

```
xilmwa@xilmwa:~$ /usr/lib/nux/unity_support_test -p  
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2
OpenGL version string:  3.3.0 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```What does it mean where it says Not blacklisted: no?

EDIT: apparently, there is a blacklist, and the nVidia 8400GS is on it. To get around this, follow the first post here: [http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity](http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity)

---

### Post by Hedgehog1 on 2011-05-14
If that does not solve it, here is one more option to try-

Please do a **<ctrl> + <alt> + t** to get the terminal.

From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

There will be some error messages - ignore them please.

Logout **<ctrl> + <alt> + <Delete>** and reboot...

***The Hedge***

:KS

---

