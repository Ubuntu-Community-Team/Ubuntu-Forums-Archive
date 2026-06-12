---
title: "Installing libgpod Cvs problem"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by damoek on 2006-12-17
I am trying to get the CVS version of gtkpod installed so i can have some video support for my ipod. I finally got all of the dependencies fixed, but when running ./autogen.sh I get a problem with 

```
checking for autoconf >= 2.53...

testing autoconf2.50...
not found.
testing autoconf...
found 2.60

checking for automake >= 1.7...

testing automake-1.7...
not found.
testing automake-1.8...
not found.
testing automake-1.9...
found 1.9.6

checking for libtool >= 1.5...

testing libtoolize...
found 1.5.22

checking for glib-gettext >= 2.2.0...

testing glib-gettextize...
found 2.12.4

checking for intltool >= 0.30...

testing intltoolize...
found 0.35.1

checking for pkg-config >= 0.14.0...

testing pkg-config...
found 0.20

checking for gtk-doc >= 1.0...

testing gtkdocize...
found 1.7

Checking for required M4 macros...

intltool.m4 not found
gtk-doc.m4 not found

Checking for forbidden M4 macros...

***Error***: some autoconf macros required to build libgpod
were not found in your aclocal path, or some forbidden
macros were found. Perhaps you need to adjust your
ACLOCAL_FLAGS?
```

I have no Idea what this means. Any help would be appreciated!

---

### Post by damoek on 2006-12-18
Ok I actually took care of that problem. However when I'm trying to configure Libgpod now with ./autogen.sh I run into a problem with intltool. I've searched everywhere, (this forum, google, etc) and I have no idea how to fix it. Does anyone have a solution that might help? 

Here is the output 
```
Running intltoolize...

intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite
```

So I tried to run intltoolize by itsself with the --force option and i get

```
ntltoolize --force
You should add the contents of '/usr/local/share/aclocal/intltool.m4' to 'aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, '..'.
intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite

```

Do I have an older version of intltool? Did I install it wrong? Please HELP! I would really like to overcome this problem

---

