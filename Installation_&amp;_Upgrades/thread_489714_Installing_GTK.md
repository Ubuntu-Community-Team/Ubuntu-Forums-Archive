---
title: "Installing GTK"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by isaacjoe on 2007-07-01
I want to install a tarball that needs GTK 2. So I search the package manager for gtk 2, and all there is is gtk-engine crap, nothing helpful. So I downloaded GTK, and it needs the Glib, Cairo, and Atk libraries. I installed Glib 2.13 following the ./configure, make, and make install instructions in its install text file. Moving down the list, tried to install Atk, and it says:

*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.


Even though I JUST installed Glib! How do I fix this, what is pkg-config, where is it?

Is there a way I can install all this mess from a package manager by adding more repositories, because ubuntu 7 looks like it's based off of a really old version of GTK. It would be much simpler than manually installing everything

---

### Post by moore.bryan on 2007-07-01
[I]it's asking for the dev package, too...
try
```
sudo aptitude install libglib2.0-0 libglib2.0-dev
```
and then do all your "make" stuff again.
[/I]

---

### Post by isaacjoe on 2007-07-02
> **moore.bryan said:**
> [I]it's asking for the dev package, too...
try
```
sudo aptitude install libglib2.0-0 libglib2.0-dev
```
and then do all your "make" stuff again.
[/I]

How did you know the exact name of the library I want? I'd like to do the same thing and install the dev GTK+ 2.0, and have it manage all the dependencies for me.

---

### Post by moore.bryan on 2007-07-03
*well, i've had the glib error before, so that helped, but it's also just a few clicks away at [packages.ubuntu.com]("http://packages.ubuntu.com/").  once on that site, just look for the key term and use a little bit of logical narrowing.  a quick look for gtk gives a bunch of packages (8 pages worth).  usually, you're looking for the libgtk2* stuff...*

---

