---
title: "Lost 3d Acceleration from 10.4 to 12.4"
date: 2013-09-10
forum: Installation &amp; Upgrades
---

### Post by balia3 on 2013-09-10
I recently upgraded Ubuntu.
Unfortunately, the upgrade didn't go smoothly.

In particular, I lost all my 3d acceleration and I haven't been able to resolve it.

I have an ATI Radeon 8500 graphic card.
[FONT=Courier New][SIZE=2]# lspci -nn | grep VGA[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] R200 [Radeon 8500/8500 LE][/SIZE][/FONT]

Normally this card is full supported by Unity
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)



Nonetheless, when I run [SIZE=2]unity_support_test -p, I get[/SIZE]
[FONT=Courier New][SIZE=2]# /usr/lib/nux/unity_support_test -p[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]OpenGL vendor string: Tungsten Graphics, Inc.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]OpenGL renderer string: Mesa DRI R200 (R200 514C) x86/MMX+/3DNow!+/SSE TCL DRI2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]OpenGL version string: 1.3 Mesa 8.0.4[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Not software rendered: yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Not blacklisted: yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]GLX fbconfig: yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]GLX texture from pixmap: yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]GL npot or rect textures: yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]GL vertex program: yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]GL fragment program: no[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]GL vertex buffer object: yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]GL framebuffer object: yes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]GL version is 1.4+: no[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Unity 3D supported: no


[/SIZE][/FONT]Any idea appreciated. Thank you.

---

### Post by lukeiamyourfather on 2013-09-10
Unity needs OpenGL 1.4 or newer and that card supports up to OpenGL 1.3, so that card won't work for the Unity 3D interface. You're not missing out on much in my opinion, Unity is just awful. You might consider LXDE or Xfce which are lighter weight than Unity and run better on older hardware.

---

### Post by balia on 2013-09-10
I installed MATE (based on GNOME 2) instead and I got it to work with Compiz.
[www.mate-desktop.org](www.mate-desktop.org)
Everything is back including the 3d acceleration and the cube.

---

### Post by lukeiamyourfather on 2013-09-11
The 3D acceleration never went away, the card was just too old to support the OpenGL version requirement of Unity. The 3D acceleration would've worked in other applications just fine even if Unity complained about it. I'm glad it's working better for you now. MATE is pretty nice!

---

### Post by tgalati4 on 2013-09-11
+1 for MATE and the win.

---

