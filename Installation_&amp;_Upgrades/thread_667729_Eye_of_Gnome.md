---
title: "Eye of Gnome"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by sisodiakris on 2008-01-14
I am trying to upgrade Eye of Gnome from 2.20.1 to 2.20.4 version. I am brand new Ubuntu user and not so crazy about "Terminal". I downloaded the eog-2.20.4.tar.gz file and using Archiving Manager extracted it to the desktop. But I don't know how to install it. I would appreciate some help. Thanks!!

---

### Post by wolfen69 on 2008-01-14
search synaptic package manager for it. i found it.

---

### Post by rodo-&gt;dave on 2008-01-14
Hi. I haven't tried eog but I assume that's the source code you got.

cd to the directory you un-tarred it into and see if there is a
autogen.sh or configure ; if there is an autogen.sh then you can type:
./autogen.sh
to start the shell

if there is a configure then type:
./configure

Hope this helps.

---

### Post by sisodiakris on 2008-01-15
It has configure file and I followed instructions. After cd to the Document folder where I extracted the folder I  typed ./configure in terminal. Nothing happened, the process didn't install the application. There has to be a way to install it.

---

### Post by rodo-&gt;dave on 2008-01-16
Here is a step by step of how I did it:

I d/led the tar file from [http://ftp.acc.umu.se/pub/GNOME/sources/eog/2.20/](http://ftp.acc.umu.se/pub/GNOME/sources/eog/2.20/)

$ tar xvfz eog*.gz
unpacks everything 

$ cd eog-2.20.4
$ ./configure
configure: WARNING: *** JPEG loader will not be built (JPEG library not found) ***
configure: error:
*** Checks for JPEG loader failed. You can build without it by passing
*** --without-libjpeg to configure but some programs using GTK+ may
*** not work properly

<I go to synaptic and search for libjpeg and then select the "-dev" for installation>
$ ./configure
No package 'gnome-vfs-2.0' found
No package 'libgnomeui-2.0' found
No package 'gconf-2.0' found
No package 'libart-2.0' found
No package 'gnome-desktop-2.0' found
Requested 'gnome-icon-theme >= 2.19.1' but version of gnome-icon-theme is 2.18.0

<I go to synaptic and install the libgnomevfs2-dev, libgnomeui-dev, libart-2.0-dev, and
 lib-gnome-desktop-dev (v1.2)>
$ ./configure
Requested 'gnome-icon-theme >= 2.19.1' but version of gnome-icon-theme is 2.18.0

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EOG_CFLAGS
and EOG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

$ vi configure
<changed line to GNOME_ICON_THEME_REQUIRED=2.18.0 cause I don't want to look for 2.19.1>
$ ./configure
$ make
$ sudo make install
  [default install dir is /usr/local/bin]
$ /usr/local/bin/eog
  Help->About v2.20.4


quite a few steps involved.. I will take wolfen69's advice and just use the one in synaptic :)
Hope this helps. Good luck.

---

### Post by sisodiakris on 2008-01-17
Thanks! for your replies.  It strengthen my belief in Linux/Ubuntu community. I would try this and post the reply soon. Thanks!

---

