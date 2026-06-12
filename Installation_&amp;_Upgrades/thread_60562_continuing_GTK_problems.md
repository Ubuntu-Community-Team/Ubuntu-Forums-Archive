---
title: "continuing GTK problems"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by aljones15 on 2005-08-28
Ok so first if someone can answer this questions:
does ubuntu come with GTK? I noticed in the package manager
that GTKlib and others are listed, but when I go to compile
programs that require gtk it says it's not there.

second, I'm trying to install gtk.
installed pango, glib, etc. I keep getting
xwindows errors regarding the libx11-dev and others.
my question being why does ubuntu not come with libx11-dev?
or does it?
I tried installing the debian packages, but they won't configure
with ubuntu's xwindows (the debian packs are one release behind
the current version of xwindows).

has anyone installed gtk on ubuntu? do i need to or do i need
to tell the programs that require it, that gtk is in a different directory?

thanks,
A

---

### Post by DJ_Max on 2005-08-28
If you're using Gnome, GTK is installed. If you want to manually compile apps, you need the gtk dev packages. Also, there's no need to manually install pango or glib, they are all in the repository. Along with libx11-dev. 

The reason it's not installed by default is to save space, and the simple fact that mostly developers are the only people that will need the extra files.

---

### Post by aljones15 on 2005-08-29
that;s strange becuase enlightment and other apps that requite gtk say it's not there, anyway, i installed glib, atk, and pango manually. hopefully that didn't **** anything up. how do i install libx11-dev? i tried the package manager but can't seem to find it.

peace,
a

maybe i need to reinstall with more support options to begin with.

---

### Post by DJ_Max on 2005-08-29
[QUOTE=aljones15]that;s strange becuase enlightment and other apps that requite gtk say it's not there, anyway, i installed glib, atk, and pango manually. hopefully that didn't **** anything up. how do i install libx11-dev? i tried the package manager but can't seem to find it.

peace,
a

maybe i need to reinstall with more support options to begin with.[/QUOTE]
 **You need the GTK development packages. This is why when compiling, configure will not find the correct dev files.**  It's something like gtk-dev. 
Glib, gtk and pango are installed by default. There was no reason for you to install them manually. 

Do a apt-cache search libx11 dev

---

