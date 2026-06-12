---
title: "Missing libcanberra module?"
date: 2009-03-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by maphilli14 on 2009-03-08
I run a customized version of coriander 1.0.0 and am now getting this message under Jaunty

```
Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
```

Anyone know if this module is in flux under jaunty?

I have the file in question via one of the libcanberra packages from dist:
```

libcanberra0                libcanberra-gtk0
libcanberra0-dbg            libcanberra-gtk0-dbg
libcanberra-dev             libcanberra-gtk-dev
libcanberra-doc             libcanberra-gtk-module
libcanberra-gnome           libcanberra-gtk-module-dbg
libcanberra-gnome-dbg       

```

I also seem to have the file in question:

```
miphilli@DRACO-V23:~$ locate libcanberra-gtk-module.s
/usr/lib/debug/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so

```

Any ideas??

TIA,

Mike

---

### Post by crimsun on 2009-03-09
According to [the control file]("http://package-import.ubuntu.com/libc/libcanberra/jaunty/annotate/head%3A/debian/control"), you should check the versions of libcanberra-gnome* installed. Jaunty's libcanberra-gtk0* has the package-fu to replace files in the former package(s).

The file "/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so" is owned by the libcanberra-gtk-module binary package. `locate' only updates once daily (or upon `updatedb' trigger), so you should actually list the file to ensure that it is installed.

Finally, is your local version of coriander compiled against an outdated libcanberra-gtk-dev?

---

