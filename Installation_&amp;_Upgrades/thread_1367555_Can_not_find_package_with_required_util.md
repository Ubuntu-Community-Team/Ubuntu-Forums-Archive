---
title: "Can not find package with required util"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by dkrig on 2009-12-29
I was going to install [xf86-input-magicmouse]("http://github.com/cosmonaut/xf86-input-magicmouse") to help in module development as I'm Magic Mouse owner and Linux user.

When I tried to configure it I got the following log:

```
$ ./autogen.sh
autoreconf2.50: Entering directory `.'
autoreconf2.50: configure.ac: not using Gettext
autoreconf2.50: running: aclocal
configure.ac:36: error: must install xorg-macros 1.3 or later before running autoconf/autogen
configure.ac:36: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: autom4te failed with exit status: 1
autoreconf2.50: aclocal failed with exit status: 1
```

I discussed this problem with module author and he suggested me to install *xutils-dev* package. I did this but I still get this error message.

Module author uses Arch Linux and the xorg-utils-macros package owns /usr/lib/pkgconfig/xorg-macros.pc for him.

I'm on Ubuntu 9.10 and can't find package that owns xorg-macros.pc or at least sources that I can build under Ubunut.

Please help me to find the package.

---

### Post by davec64 on 2009-12-29
I dont know what your talking about but thought I'd have a search and see what I could find!

The following package:

xutils-dev

Contains:

> contains xorg-macros.m4, a set of macros used in configure scripts of X.Org packages 

I found the details here:
[http://packages.ubuntu.com/karmic/xutils-dev]("http://packages.ubuntu.com/karmic/xutils-dev")

Ignore my post if it's of no use!

Best of luck!

---

### Post by cristianku on 2010-01-04
hi same problem here, i tried the installation as proposed using synaptics but no results

still getting the error about the xorg-macros 1.3 to be installed

---

### Post by SimonPe on 2010-01-31
hey

i found the same problem and also the solution:
download and install the xutils-dev package from lucid

[http://packages.ubuntu.com/lucid/xutils-dev](http://packages.ubuntu.com/lucid/xutils-dev)

this one contains a newer version of the xorg-macros

---

### Post by monstara on 2010-02-24
Thanks SimonPe, your solution worked!

---

### Post by quxtilf on 2010-03-24
You'll be also no 'xorg-macros.pc' file after installing xutils-dev package by typing:
$ sudo apt-get install xutils-dev
because it gets a different version excluding the file xorg-macros.pc.

The correct method is as below,
(e.g.)
$ wget [http://mirrors.kernel.org/ubuntu/pool/main/x/xutils-dev/xutils-dev_7.5+2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/x/xutils-dev/xutils-dev_7.5+2_i386.deb)
$ sudo dpkg -r xutils-dev
$ sudo dpkg -i xutils-dev_7.5+2_i386.deb
Then you can find the file in /usr/share/pkgconfig directory.

OS: Ubuntu Linux 9.10

---

