---
title: "slow scrolling -ubuntu 9.04"
date: 2009-02-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ubusira on 2009-02-01
upgrated yesterday from 8.10 to 9.04 jaunty.

I get very slow scrolling in every kind of terminal console
(terminal, terminator,etc)
and in firefox e.g. (bookmark scrolling)

please Help 

:(

---

### Post by taavikko on 2009-02-01
issue is probably related to graphics card drivers.
check them.

Jaynty is still in alpha state, be warned that it is not recommended for inexperienced users and/or production machines.

---

### Post by Mazza558 on 2009-02-01
ATI graphics card?

---

### Post by tala on 2009-02-01
I am getting the exact same scenario
i think its using software instead of hardware for the OpenGL
but i dont know which Nvidia drivers to install 
i am on a HP-510 laptop

---

### Post by Starks on 2009-02-01
Confirming for Intel too.

It was never this slow before.

---

### Post by ubusira on 2009-02-02
ok my friends.thanks for your posts.
I'm trying to fix this.

_hp compaq 6820s laptop.-ati mobility radeon X1350._

---

### Post by ubusira on 2009-02-02
ok here we are.
download xserver-xorg-video-radeonhd_1.2.4.orig.tar.gz
from [https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-radeonhd:p](https://launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-radeonhd:p)
extract in root.


Installation
============

With X.Org 7.0 and later:

   $ ./autogen.sh
   $ make
   $ make install

This will litter all kinds of compiled files throughout your source tree.

OR

With X.Org prior to 7.0:

apt-get install xutils-dev



   $ xmkmf -a
   $ make EXTRA_INCLUDES="-I/usr/include/xorg" all
   $ make install


it works for me now in Jaunty ok!!

---

### Post by ubusira on 2009-02-02
[https://launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-radeonhd/1.2.4-1:o](https://launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-radeonhd/1.2.4-1:o)

---

### Post by ubusira on 2009-02-02
sorry folks, i dont know whats going on but i tested last post
and didnt  give the link


so once again.

//launchpad.net/ubuntu/jaunty/+package/xserver-xorg-video-radeonhd

add http....

---

