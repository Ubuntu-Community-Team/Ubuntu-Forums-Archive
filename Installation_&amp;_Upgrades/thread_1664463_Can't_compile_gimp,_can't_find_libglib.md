---
title: "Can't compile gimp, can't find libglib"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by Mark20 on 2011-01-11
Hi all,

I'm trying to compile gimp on ubuntu 9.10 and I'm stuck during the ./configure stage I'm getting the following:

```
checking for GLIB - version >= 2.24.0... no
*** Could not run GLIB test program, checking why...
*** The test program compiled, but did not run. This usually means
```

The config.log complains that it's missing glib.h.

After verifying that I have the development library I'm still getting this problem.  I did the following and saw that both libglib, and the development library showed the state "INSTALLED":

```
aptitude show libglib2.0-0 libglib2.0-dev
```

Despite this, I can't find the .pc file for libglib2.0-dev anywhere:

mark@mark-home:~/workspace/gimpsrc/gimp-2.7.1$ find /usr -name *.pc | grep glib*
/usr/lib/pkgconfig/glib-2.0.pc
/usr/lib/pkgconfig/ndesk-dbus-glib-1.0.pc
/usr/lib/pkgconfig/glib-sharp-2.0.pc
/usr/share/pkgconfig/taglib-sharp.pc

If aptitude shows libglib2.0-dev installed the pc file must exist somewhere... anyone have any ideas as to how to verify that libglib2.0-dev is installed correctly?

Thanks,
Mark

---

### Post by ikt on 2011-01-11
> **Mark20 said:**
> Hi all,

I'm trying to compile gimp on ubuntu 9.10 and I'm stuck during the ./configure stage I'm getting the following:


Any reason why you're trying to install gimp from source instead of via the repos?

Also do you have build-essential installed?

---

### Post by lykeion on 2011-01-11
Have you checked that you installed all the required dev packages to compile: [http://www.gimp.org/source/](http://www.gimp.org/source/)
And also the packages needed to compile software: [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

But if you would like the easy way to get the latest svn version of GIMP there is a PPA here: 
[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn?field.series_filter=karmic](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn?field.series_filter=karmic)

---

### Post by Mark20 on 2011-01-11
Thanks for the replies so far,

@ikt
Yes I'm interested in testing some color filter algorithms I've been working on and I figured gimp would be an quick and easy way to test the algorithms by simply making a plugin and running it in gimp.  I'm not sure if I have build-essentials installed, I'll check when I get home.

@lykeion
Yeah I made sure I had installed all of the requirements, however like I said I'm not convinced that libglib2.0-dev is installed correctly since the .pc file is not installed anywhere on my system, and during ./configure the libglib2.0-dev package is not found anywhere.

Is there a way to find out where an installed package's .pc file is located?  Any other ideas?

Mark

---

### Post by Mark20 on 2011-01-11
This is now resolved.

libglib was actually installed correctly the whole time but I did not have a new enough version of libglib/libgtk.  I'm guessing -dev packages do not have corresponding .pc files.

I then attempted to fix the sources.list file to grab the newer libglib/libgtk however the newer versions are not available yet and I didn't feel like wasting another hour trying to hack together a system with the new packages manually so I downloaded an earlier version of gimp and everything builds fine now :)

Mark

---

### Post by gmargo on 2011-01-11
> **Mark20 said:**
> Is there a way to find out where an installed package's .pc file is located? 

```

$ dpkg -L libglib2.0-dev | grep '\.pc$'
/usr/lib/pkgconfig/glib-2.0.pc
/usr/lib/pkgconfig/gobject-2.0.pc
/usr/lib/pkgconfig/gmodule-2.0.pc
/usr/lib/pkgconfig/gmodule-export-2.0.pc
/usr/lib/pkgconfig/gmodule-no-export-2.0.pc
/usr/lib/pkgconfig/gthread-2.0.pc
/usr/lib/pkgconfig/gio-2.0.pc
/usr/lib/pkgconfig/gio-unix-2.0.pc

```
(this list is from 10.10 Maverick)

---

