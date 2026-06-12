---
title: "Which packages to install"
date: 2019-02-27
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2019-02-27
i want to get this stuff installed but they never tell the names of Ubuntu packages.  well, for some things and some distros, package names do get displayed. i don't really know a good solution other than have the writer(s) show package names for all distros, or at at least for Ubuntu.

this is my project of the day:  [https://python-gtk-3-tutorial.readthedocs.io/en/latest/install.html](https://python-gtk-3-tutorial.readthedocs.io/en/latest/install.html)

does anyone know which Ubuntu packages to install for the above?

---

### Post by bitsnpcs on 2019-02-28
Hello Skaperen,

I am not sure how to list the package names.

What I did was look here [https://pygobject.readthedocs.io/en/latest/getting_started.html](https://pygobject.readthedocs.io/en/latest/getting_started.html)

It gives a sample Hello-World code then says - 
"Before we can run the example application we need to install PyGObject, GTK and their dependencies. Follow the instructions for your platform below." <<< you do not need to follow the instructions (I've always wanted to write that lol)

Copying the code as it is, in to Gedit saving and then running in terminal works correctly , this tells me PyGObject, GTK and their dependencies are already installed, and you can begin your project of the day now :)
[https://ibb.co/9vVV40K](https://ibb.co/9vVV40K)

I added 8 spaces to the sample code on the website link, line #5 after *world* inside the " , then it appears with the name in title bar looking better -
[https://ibb.co/QY2W22m](https://ibb.co/QY2W22m)

---

### Post by The Cog on 2019-02-28
This is a good way to look for packages when you don't know the name: **apt search PyGObject**
For me it gave:
```
~$  apt search PyGObject
Sorting... Done
Full Text Search... Done
python-gi-dev/xenial 3.20.0-0ubuntu1 amd64
  development headers for GObject Python bindings

python-glade2/xenial 2.24.0-4ubuntu1 amd64
  GTK+ bindings: Glade support

python-gobject-2-dev/xenial,xenial 2.28.6-12ubuntu1 all
  development headers for the static GObject Python bindings

python-gtk2/xenial,now 2.24.0-4ubuntu1 amd64 [installed,automatic]
  Python bindings for the GTK+ widget set

python-gtk2-dbg/xenial 2.24.0-4ubuntu1 amd64
  Python bindings for the GTK+ widget set (debug extension)

python-gtk2-dev/xenial,xenial 2.24.0-4ubuntu1 all
  GTK+ bindings: devel files

python-gtk2-doc/xenial,xenial 2.24.0-4ubuntu1 all
  Python bindings for the GTK+ widget set - documentation

python-gtkspellcheck/xenial,xenial 3.0-1.1 all
  spellchecking library written in Python for Gtk based on Enchant

python-gtkspellcheck-doc/xenial,xenial 3.0-1.1 all
  Python GTK Spellcheck common documentation

python3-gtkspellcheck/xenial,xenial 3.0-1.1 all
  spellchecking library written in Python for Gtk based on Enchant


```

---

### Post by Skaperen on 2019-02-28
it would be nice to have an absolute one to one mapping of project to package.   but i suppose that can never really happen due to some project name overlap. OTOH, if we could establish an international project name committee to handle overlaps as name disputes (never happen ... politics) then this could be resolved.

---

### Post by Skaperen on 2019-02-28
> **The Cog said:**
> This is a good way to look for packages when you don't know the name: **apt search PyGObject**
For me it gave:
```
~$  apt search PyGObject
...


```

is there a way to do that for other releases, such that one server can do that for trusty, xenial, bionic, and cosmic?

---

### Post by Holger_Gehrke on 2019-02-28
> **Skaperen said:**
> is there a way to do that for other releases, such that one server can do that for trusty, xenial, bionic, and cosmic?

'apt search' is searching the local package lists in '/var/lib/apt/lists'. And since those are tied to the  release of Ubuntu currently running on the machine you can't search for packages from other releases.

You can of course search for packages in any release at [packages.ubuntu.com]("https://packages.ubuntu.com") .

Holger

---

