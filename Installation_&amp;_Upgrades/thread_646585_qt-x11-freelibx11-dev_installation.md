---
title: "qt-x11-free/libx11-dev installation"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by malkateb on 2007-12-21
Hi,

I'm using Linux Ubuntu 7.10.

I'm trying to install qt-x11-free.

I've successfully run the command "./configure". 

But when I run the command "make", I got the following errors:

<begin>
Now, when I run the command "make", I get the following errors:
kernel/qt_x11_p.h:66:22: error: X11/Xlib.h: No such file or directory
kernel/qt_x11_p.h:71:23: error: X11/Xutil.h: No such file or directory
kernel/qt_x11_p.h:72:21: error: X11/Xos.h: No such file or directory
kernel/qt_x11_p.h:73:23: error: X11/Xatom.h: No such file or directory
make[2]: *** [.obj/release-shared/qtaddons_x11.o] Error 1
make[2]: Leaving directory `/home/malkateb/qt/src'
make[1]: *** [sub-src] Error 2
make[1]: Leaving directory `/home/malkateb/qt'
make: *** [init] Error 2
<end>

To overcome these errors, I tried to install the package  "libx11-dev" using the following command:

sudo apt-get install libx11-dev

but, I get the following error:
E: Couldn't find package libx11-dev

Any idea to help? Thanks.

---

### Post by Partyboi2 on 2007-12-22
check your /etc/apt/sources.list and make sure that everything that is meant to be enabled is. If not sure how to do that post the contents of your source.list
Another way is to go to this site and manually download the package and install by double clicking
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libx11-dev&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libx11-dev&searchon=names&subword=1&version=all&release=all)

---

### Post by malkateb on 2007-12-25
Thanks. 

I managed to overcome the problem. 

I had to:

1- uncomment the relevant lines in the "/etc/apt/sources.list" file and after that,
2- execute this command "sudo apt-get update"

These two steps solved the problem!

---

