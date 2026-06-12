---
title: "Unity Not Supported? Not blacklisted=no"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by BrumleyGap on 2011-04-29
I booted 11.04 from a USB and ran the unity_support_test to see why Unity was not running.

I need help understanding what "Not blacklisted" means.

ubuntu@ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV46
OpenGL version string:  2.1 Mesa 7.10.2

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

---

### Post by falsehope on 2011-05-02
Same exact issue!

My video card is: Nvidia GeForce Go 7300

Compiz wont even work in Ubuntu 11.04 now.

Can someone please explain "Not blacklisted = no".

I made sure that this driver is not blacklisted at /etc/modprobe.d/*


Here my out of the support script:
falsehope@D620:~$ /usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV46
OpenGL version string:  2.1 Mesa 7.10.2

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

---

### Post by Onesimus on 2011-05-03
I have exactly same graphics card.

The graphics driver has been blacklisted in nvidia-graphics-drivers.conf

Not sure when we will see a solution to this.  I have installed unity-2d
```

sudo apt-get install unity-2d
```

so that I can use unity in the short term.

---

### Post by Onesimus on 2011-05-03
Just found this info on it:

[http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity]("http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity")

---

