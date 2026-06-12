---
title: "GL stopped working with todays updates"
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vhaarr on 2010-01-12
Hey,

I recently filed a bug in launchpad because with todays updates, 3D apps no longer work through WINE.

The relevant bug report is at [https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/506320](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/506320), and I tried to include as much information as I could.

The thing is, I'm not sure if maybe my system is full of old symlinks or stuff that breaks all this? Perhaps I need to fix it locally only?

Anyone else having similar problems?

---

### Post by taavikko on 2010-01-12
It's not an issue with WINE.
All gl is affected, so the pointing finger goes to mesa.

after this update things went haywire.
[UPGRADE] libgl1-mesa-dri 7.7-0ubuntu3 -> 7.7-0ubuntu4
[UPGRADE] libgl1-mesa-glx 7.7-0ubuntu3 -> 7.7-0ubuntu4
[UPGRADE] xserver-common 2:1.7.3.902-1ubuntu2 -> 2:1.7.3.902-1ubuntu4
[UPGRADE] xserver-xorg-core 2:1.7.3.902-1ubuntu2 -> 2:1.7.3.902-1ubuntu4

---

### Post by vhaarr on 2010-01-12
> **taavikko said:**
> It's not an issue with WINE.
All gl is affected, so the pointing finger goes to mesa.

Can't be all GL, since native 3D applications work just fine.

It's probably only the 32bit libraries that are not working properly at this point, so I'm guessing the problem is in ia32-libs?

---

### Post by MadMan2k on 2010-01-12
its xserver-xorg-core which cant find the GLX and DRI modules any more.
workaround:
```

cd /usr/lib/xorg/modules/
sudo ln -s extensions/libdri.so
sudo ln -s extensions/libdri2.so
sudo ln -s extensions/libglx.so

```

---

### Post by vhaarr on 2010-01-12
> **MadMan2k said:**
> its xserver-xorg-core which cant find the GLX and DRI modules any more.
workaround:
```

cd /usr/lib/xorg/modules/
sudo ln -s extensions/libdri.so
sudo ln -s extensions/libdri2.so
sudo ln -s extensions/libglx.so

```

This was possibly a solution to the older problems from yesterday.

Today, this is not the problem.

---

### Post by taavikko on 2010-01-12
> **MadMan2k said:**
> its xserver-xorg-core which cant find the GLX and DRI modules any more.
workaround:
```

cd /usr/lib/xorg/modules/
sudo ln -s extensions/libdri.so
sudo ln -s extensions/libdri2.so
sudo ln -s extensions/libglx.so

```

Not working since lib{glx,dri}.so are missing...

the new xorg is available through updates, let's see if fixes the issue...

---

### Post by taavikko on 2010-01-12
> **taavikko said:**
> Not working since lib{glx,dri}.so are missing...

the new xorg is available through updates, let's see if fixes the issue...

Yep, the new [UPGRADE] xserver-xorg-core 2:1.7.3.902-1ubuntu4 -> 2:1.7.3.902-1ubuntu5
Brought both missing files back, so it's working for me again.

Hope it works again for vhaarr too :)

---

### Post by vhaarr on 2010-01-12
It's only with 32bit applications I have problems.

xorg w/ compiz, quake1 native, scorch3d, etc, they all work fine.

---

### Post by VMC on 2010-01-12
> **taavikko said:**
> Yep, the new [UPGRADE] xserver-xorg-core 2:1.7.3.902-1ubuntu4 -> 2:1.7.3.902-1ubuntu5
Brought both missing files back, so it's working for me again.

Hope it works again for vhaarr too :)

Hey thanks for pointing that out. "4" is where it failed for me. I guess "4" was more wide spread than I thought. Hopefully "5" will fix my black screen.

edit: Great, its fixed! Thanks again taavikko for pointing this out. I wasn't going to do anymore updates, fearing for the worse. So now removing "nomodeset" and putting grub back to normal, all is well....right now anyway.

---

### Post by SevenMachines on 2010-01-12
ia32-libs needs to be updated to use alternatives for libGL which i'm guessing is causing the wine problem, alberto milone is working on this (see [https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/494166/comments/53](https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/494166/comments/53))

[EDIT] actual relevant ia32-libs bug [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/506435](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/506435)

---

### Post by vhaarr on 2010-01-12
> **SevenMachines said:**
> 
[EDIT] actual relevant ia32-libs bug [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/506435](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/506435)

Thanks!

Also relevant is [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/506437](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/506437)

---

### Post by moviemaniac on 2010-02-17
Could it be that GL depends on Plymouth? I had to uninstall plymouth due to many system freezes and since then (well, I think so but it could as well be some other glitch as I don't play games on a daily basis) I can't play any game depending on GL (Openarena, TORCS, also games using WINE). Oh, and I also disabled KMS but when I enabled it as a test GL also didn't work so that shouldn't be the issue.

my /usr/lib/xorg/modules looks like this:

> klaus@klaus-imac:/usr/lib/xorg/modules$ ls
drivers  extensions  input  libexa.so  libfb.so  libint10.so  libshadowfb.so  libshadow.so  libvbe.so  libvgahw.so  libwfb.so  libxaa.so  libxf8_16bpp.so  linux  multimedia
klaus@klaus-imac:/usr/lib/xorg/modules$ cd extensions
klaus@klaus-imac:/usr/lib/xorg/modules/extensions$ ls
libdbe.so  libdri2.so  libdri.so  libextmod.so  libglx.so  librecord.so


---

