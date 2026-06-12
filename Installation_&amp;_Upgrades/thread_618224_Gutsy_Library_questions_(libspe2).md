---
title: "Gutsy Library questions (libspe2)"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by mickfromperth on 2007-11-20
Hi Gang,

I have a ps3 running ubuntu, and am attempting to compile some bleeding edge code for it..  it says I need libspe2.  So I went and apt-get-ed the following:

---
mick@mick-desktop:~/build/spu-medialib$ sudo apt-get install libspe2
Reading package lists... Done
Building dependency tree
Reading state information... Done
libspe2 is already the newest version.
libspe2 set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
mick@mick-desktop:~/build/spu-medialib$ sudo apt-get install libspe2-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
libspe2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
---

When I compile the code, it says libspe2 not found.  I've dug down and discovered the source of the issue is libspe2's missing a "pkg-config".  I'm a relative newb, but I get the impression that the .pc file is  normally installed in the name-dev package; which I have installed..  So I think it's missing from the package?

---
mick@mick-desktop:~/build/spu-medialib$ sudo pkg-config --cflags --libs libspe2
Package libspe2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libspe2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libspe2' found
---

Is there a way to hack together a *.pc file?  Whats the format?  How does one report this issue to get fixed?

Mick

---

### Post by mickfromperth on 2007-11-20
< friendly bump>

---

### Post by mickfromperth on 2007-11-21
< friendly bump >

---

