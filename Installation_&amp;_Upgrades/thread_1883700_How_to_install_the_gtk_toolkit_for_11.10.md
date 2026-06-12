---
title: "How to install the gtk toolkit for 11.10?"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by kline on 2011-11-19
hi people,

i have searched for hours about installing gtk+ on my ubuntu 11.10 so i can begin teaching myself how to develop some GUI tools.  so far, nothing.  one tutorial program in C has:

#include <gtk/gtk.h>

which breaks immediately because there is no gtk directory in /usr/include.  so my first question is how to install a package -- or even src -- that will install the latest gtk libraries.  

any development wizards out there?

thans in advance.

---

### Post by shansen5 on 2011-11-20
Similar question.  I'm trying to build a little game that I downloaded.  It has a configure script that tests my system--newly installed Ubuntu 11.10.  

checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... no
configure: error: GTK+-2.14 is required to compile

---

### Post by shansen5 on 2011-11-20
Just:
sudo apt-get install libgtk2.0-dev

---

### Post by kline on 2011-11-20
(tutorial:13792): Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

is what i got [?]

---

