---
title: "v86 with uvesafb Ubuntu Karmic"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dschaefer79 on 2009-10-23
Hi,

I want to use v86d with uvesafb with a resolution of 1920x1200 for the console. How can I setup this ? I'm on Ubuntu Karmic.

I tried to install v86d via apt-get install v86d. but I don't know now how to setup.

Can someone help me ? Thanks.

Dominique

---

### Post by dschaefer79 on 2009-10-23
dmesg | grep uvesafb
that give me this.

[   10.452341] uvesafb: NVIDIA Corporation, GT200 Board - 0654s051, Chip Rev   , OEM: NVIDIA, VBE v3.0
[   11.708026] uvesafb: VBIOS/hardware doesn't support DDC transfers
[   11.708028] uvesafb: no monitor limits have been set, default refresh rate will be used
[   11.708272] uvesafb: scrolling: redraw
[   11.708612] uvesafb: framebuffer at 0xf9000000, mapped to 0xffffc90014580000, using 14336k, total 14336k
[   33.415772] uvesafb: mode switch failed (eax=0x14f, err=0)
[   33.419482] uvesafb: mode switch failed (eax=0x14f, err=0)
[  376.409414] uvesafb: mode switch failed (eax=0x14f, err=0)
[  382.638177] uvesafb: mode switch failed (eax=0x14f, err=0)
[  382.645056] uvesafb: mode switch failed (eax=0x14f, err=0)
[  382.649958] uvesafb: mode switch failed (eax=0x14f, err=0)
[  405.658195] uvesafb: mode switch failed (eax=0x14f, err=0)
[ 1839.807978] uvesafb: mode switch failed (eax=0x14f, err=0)
[ 1909.643462] uvesafb: mode switch failed (eax=0x14f, err=0)
[ 1933.516928] uvesafb: mode switch failed (eax=0x14f, err=0)
[ 2160.987139] uvesafb: mode switch failed (eax=0x14f, err=0)
[ 2192.962308] uvesafb: mode switch failed (eax=0x14f, err=0)
[ 2199.998713] uvesafb: mode switch failed (eax=0x14f, err=0)
[ 2268.080990] uvesafb: mode switch failed (eax=0x14f, err=0)

Is it a kernel bug ?

---

