---
title: "Update notification daemon Dunst from 0.2.0-1 to 1.2.0."
date: 2017-08-18
forum: Installation &amp; Upgrades
---

### Post by darkskylord88 on 2017-08-18
Update notification daemon Dunst from 0.2.0-1 to 1.2.0.

In Ubuntu 12.10 Quantal i have old version of Dunst - 0.2.0-1.
Download new 1.2.0 from [https://github.com/dunst-project/dunst/archive/v1.2.0.tar.gz](https://github.com/dunst-project/dunst/archive/v1.2.0.tar.gz)
Extract to ~/src/dunst-1.2.0
Type make
see Package "dbus-1" was not found in the pkg-config search path
type sudo apt-get install libdbus-1-dev

Good, but next is Package glib-2.0 was not found in the pkg-config search path
sudo apt-cache search glib
sudo apt-get install libglib2.0-0 libglib2.0-dev
Requested 'glib-2.0 >= 2.36' but version of GLib is 2.34.1
sudo apt-get install libpango1.0-0 libpango1.0-dev
Good.

sudo apt-get install gir1.2-gdkpixbuf-2.0 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdk-pixbuf2.0-dev libgdkcutter-pixbuf0
sudo apt-get install libgtk2.0-dev libglib2.0-dev - GOOOOOOOD!
/usr/lib/i386-linux-gnu/pkgconfig/gdk-2.0.pc

make
Requested 'glib-2.0 >= 2.36' but version of GLib is 2.34.1
config.mk:50: *** "pkg-config failed, see errors above".  Stop.

cat /usr/lib/i386-linux-gnu/pkgconfig/glib-2.0.pc
Name: GLib
Description: C Utility Library
Version: 2.34.1

I open config.mk and change glib-2.0 >= 2.36 to 2.34 in pkg_config_packs
Type make and
```

cc -o src/x11/screen.o -c src/x11/screen.c -g --std=gnu99 -pedantic -Wall -Wno-overlength-strings -Os  -D_DEFAULT_SOURCE -DVERSION=\""1.2.0 (2017-07-12)"\" -pthread -I/usr/include/dbus-1.0 -I/usr/lib/i386-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gtk-2.0 -I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/gdk-pixbuf-2.0   -I.
src/x11/screen.c: In function ‘randr_update’:
src/x11/screen.c:102:9: error: unknown type name ‘XRRMonitorInfo’
src/x11/screen.c:102:9: warning: implicit declaration of function ‘XRRGetMonitors’ [-Wimplicit-function-declaration]
src/x11/screen.c:102:29: warning: initialization makes pointer from integer without a cast [enabled by default]
src/x11/screen.c:113:40: error: request for member ‘x’ in something not a structure or union
src/x11/screen.c:114:40: error: request for member ‘y’ in something not a structure or union
src/x11/screen.c:115:40: error: request for member ‘width’ in something not a structure or union
src/x11/screen.c:116:40: error: request for member ‘height’ in something not a structure or union
src/x11/screen.c:117:42: error: request for member ‘mheight’ in something not a structure or union
src/x11/screen.c:120:9: warning: implicit declaration of function ‘XRRFreeMonitors’ [-Wimplicit-function-declaration]
make: *** [src/x11/screen.o] Error 1

```

I downloaded [https://ftp.gnome.org/pub/gnome/sources/glib/2.36/glib-2.36.4.tar.xz](https://ftp.gnome.org/pub/gnome/sources/glib/2.36/glib-2.36.4.tar.xz)
unpack and
grep -Ril "XRRMonitorInfo" ./
grep -Ril "XRRGetMonitors" ./
Nothing. Hmmm, these functions are not in glib 2.36!

I find [https://cgit.freedesktop.org/xorg/lib/libXrandr/tree/src/XrrMonitor.c](https://cgit.freedesktop.org/xorg/lib/libXrandr/tree/src/XrrMonitor.c) - there are XRRMonitorInfo, XRRGetMonitors and XRRFreeMonitors code.
I type sudo find / -iname XrrMonitor.c and nothing.

I need to update libxrandr!
What version of libxrandr have I?

dpkg -L libxrandr-dev
Output are
```

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libxrandr-dev
/usr/share/doc/libxrandr-dev/copyright
/usr/share/man
/usr/share/man/man3
/usr/share/man/man3/Xrandr.3.gz
/usr/lib
/usr/lib/i386-linux-gnu
/usr/lib/i386-linux-gnu/pkgconfig
/usr/lib/i386-linux-gnu/pkgconfig/xrandr.pc
/usr/lib/i386-linux-gnu/libXrandr.a
/usr/include
/usr/include/X11
/usr/include/X11/extensions
/usr/include/X11/extensions/Xrandr.h
/usr/share/doc/libxrandr-dev/changelog.Debian.gz
/usr/share/man/man3/XRRSelectInput.3.gz
/usr/share/man/man3/XRRGetScreenInfo.3.gz
/usr/share/man/man3/XRRRootToScreen.3.gz
/usr/share/man/man3/XRRFreeScreenConfigInfo.3.gz
/usr/share/man/man3/XRRConfigCurrentConfiguration.3.gz
/usr/share/man/man3/XRRQueryVersion.3.gz
/usr/share/man/man3/XRRConfigSizes.3.gz
/usr/share/man/man3/XRRConfigCurrentRate.3.gz
/usr/share/man/man3/XRRConfigTimes.3.gz
/usr/share/man/man3/XRRSetScreenConfigAndRate.3.gz
/usr/share/man/man3/XRRConfigRotations.3.gz
/usr/share/man/man3/XRRSetScreenConfig.3.gz
/usr/share/man/man3/XRRQueryExtension.3.gz
/usr/share/man/man3/XRRConfigRates.3.gz
/usr/lib/i386-linux-gnu/libXrandr.so

```

cat /usr/lib/i386-linux-gnu/pkgconfig/xrandr.pc
Name: Xrandr
Description: X RandR Library
Version: 1.4.0

[https://launchpad.net/ubuntu/+source/libxrandr/+publishinghistory](https://launchpad.net/ubuntu/+source/libxrandr/+publishinghistory)
Last update of package libxrandr for Ubuntu 12.10 Quantal (version 2:1.4.0-1ubuntu0.1) is 2015-04-24 11:19:49 UTC.

I have 1.4.0 version of libxrandr.

I downloaded all *.c and *.h files from [https://cgit.freedesktop.org/xorg/lib/libXrandr/tree/src](https://cgit.freedesktop.org/xorg/lib/libXrandr/tree/src) and put them into /home/vova/src/dunst-1.2.0/src
make - and error that "src/x11/XrrMonitor.c:157:5: error: unknown type name ‘xRRSetMonitorReq’"
I am doing something wrong, it will be easily way to update libxrandr.

Best regards, Vladimir

---

