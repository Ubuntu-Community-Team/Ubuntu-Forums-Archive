---
title: "No unity - just wallpaper and cursor after login - Ubuntu 14.04"
date: 2015-03-14
forum: Installation &amp; Upgrades
---

### Post by orange2k on 2015-03-14
After installation of Ubuntu 14.04 in nomodeset mode and instalation of nvidia-current drivers, I get no unity or panel after login...

I have a dual boot of Windows 7 and Ubuntu 14.04, and Win 7 is working just fine...

I am beginning to think its a hardware problem since I didn't have this problem ever before, and I installed Ubuntu the same way every time...

I have an Athlon x2 4400 processor, integrated Nvidia graphics (GeForce 6150 nforce 430) with 128MB shared memory, 2,5 GB RAM...

However, I can get into unity by entering nomodeset in grub before booting, but then I get 640x480 resolution only...

What should I try to do to make it work?

---

### Post by orange2k on 2015-03-14
Update: nomodeset is not working with nvidia-current drivers installed, I had to purge the drivers with sudo apt-get purge nvidia-*  ...to be able to get past login...

Another update: with nomodeset in grub I managed to install gnome-shell and nvidia-current drivers again, and gnome-shell is working!!!

hooray, but I'm quite surprised not to be able to get unity to start...

---

### Post by grahammechanical on 2015-03-14
Ubuntu will install the latest stable proprietary video drivers but do they still support older video cards? Nvidia and AMD are in the habit of dropping support for what they consider obsolete hardware.

Another thing to consider is whether that graphic adaptic is capable of doing 3D accelerated video rendering in hardware which is a requirement for Unity. If not then everything has to be done by the CPU. To test Unity suitablility run

```
/usr/lib/nux/unity_support_test -p
```

Regards.

---

### Post by orange2k on 2015-03-14
That test gives the following output:

```
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 6150SE nForce 430/integrated/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.125

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

But I still can't log into unity...:(

---

### Post by ubfan1 on 2015-03-14
Do you get Unity when using the guest session?  Sometimes the .config/... gets messed up, and the guest session should have a good one.

---

### Post by orange2k on 2015-03-14
> **ubfan1 said:**
> Do you get Unity when using the guest session?  Sometimes the .config/... gets messed up, and the guest session should have a good one.

No, I still get only the wallpaper with the mouse pointer... :(

---

### Post by Bashing-om on 2015-03-14
orange2k; Hi !


A thought; What driver are you installing ?
The 304.xx driver supports the following set of GPUs:
GeForce 6150SE nForce 430	0x03D0
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

[INDENT][INDENT]else, it is fault isolation time
[/INDENT][/INDENT]

---

### Post by orange2k on 2015-03-14
Yes, I did install the 304.xxx - Nvidia current driver, like I always do when I install Ubuntu...
It must be some kind of undetected hardware error, because I did the installation more than once on this machine, and I always installed the same drivers...

---

### Post by orange2k on 2015-03-15
Another update - I installed KDE-standard, and even KDE works with all the effects...

Strange not to be able to use Unity...

---

