---
title: "gkrellm 2.2.9 &amp; gkrelltop 2.6"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by Camino on 2006-06-15
Hello Community,
maybe someone can help installing the lastest gkrellm 2.2.9.

I downloaded the source package from their homepage and I tried to make the packages but it gives me different error messages.

[quote]
 make
(cd po && make all)
make[1]: Entering directory `/usr/local/src/gkrellm-2.2.9/po'
make[1]: Für das Ziel »all« ist nichts zu tun.
make[1]: Leaving directory `/usr/local/src/gkrellm-2.2.9/po'
(cd src && make gkrellm)
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
make[1]: Entering directory `/usr/local/src/gkrellm-2.2.9/src'
cc -Wall -O2 -I.. `pkg-config --cflags gtk+-2.0 gthread-2.0`   -DENABLE_NLS -DLOCALEDIR=\"/usr/local/share/locale\"    -c -o main.o main.c
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gthread-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gthread-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gthread-2.0' found
In Datei, eingefügt von main.c:22:
gkrellm.h:30:21: Fehler: gtk/gtk.h: No such file or directory
make[1]: *** [main.o] Interrupt
make: *** [all] Interrupt
...
[/qoute]

Anybody knows how I can I point the make call to my gtk2 ?

The same errors I´m getting with gkrellmtop ;)

Regards

---

### Post by taurus on 2006-06-15
Looks like you need to install gtk-dev before you can build it!!!  Use the Search button in synaptic to find it...

---

### Post by Camino on 2006-06-15
wow, that was easy :)

thanks for your help...managed now to get them installed

had to install the xorg-dev packages too

Regards

Camino

---

### Post by taurus on 2006-06-15
See how easy it was if you just include the error message!  ;)

---

