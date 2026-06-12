---
title: "Compiling gtk+"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by bustanil on 2007-10-23
Hi... I'm trying to compile gtk+-2.10.13..
I've successfully compiled and installed glib, atk, pango, libtiff and libjpeg.
But when I'm configuring gtk+-2.10.13 using the command ./configure.. It gave me this error messages..

checking for jpeg_destroy_decompress in -ljpeg... yes
checking for jpeglib.h... no
configure: WARNING: *** JPEG loader will not be built (JPEG header file not found) ***
configure: error:
*** Checks for JPEG loader failed. You can build without it by passing
*** --without-libjpeg to configure but some programs using GTK+ may
*** not work properly

I've copied the jpeglib.h from the libjpeg source dir to /usr/include and /usr/local/incude but it has no effect..

Can anyone tell me... where should I copy it?

---

### Post by FredB on 2007-10-23
Try to install dev packages related to libgtk :

```
sudo apt-get builddep libgtk2.0-0
```

---

### Post by Boomloko on 2007-10-24
ok...now when i try it i get this!
boomloko@boomloko-laptop:~$ sudo apt-get build-dep  libgtk2.0-0
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to find a source package for gtk+2.0
boomloko@boomloko-laptop:~$
...anybody?!please

---

