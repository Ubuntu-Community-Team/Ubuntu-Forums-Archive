---
title: "apt-get command for gtk..."
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by ralph4100 on 2005-11-18
Does anyone know the apt command to install gtk:

```
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
checking for gtk-config... (cached) no
checking for GTK - version >= 1.0.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: GUI library not found

```

---

### Post by aysiu on 2005-11-18
What do you mean by install Gtk? Doesn't Gnome use Gtk by default... ?

---

### Post by ralph4100 on 2005-11-18
I just figured *something* needed to be installed because of the error message I got... If it's not gtk then why did I get that error message?

---

### Post by 8086 on 2005-11-18
[QUOTE=ralph4100]
Does anyone know the apt command to install gtk:
[/quote]
There is no "apt command to install gtk" per se, it is just the usual
1. Find name of package
2. sudo apt-get install "name-of-package" (or use synaptic)

To find the name of the gtk-package you can either search using synaptic, or for instance 
"apt-cache search gtk|grep gtk|less"
which will find most packages relating to gtk. Should be easy to spot the right one. (This is what I did).

> 
```
checking for GTK - version >= 1.2.0... no
<snip>

```
This is kind of misleading in a way;
You do have gtk2.0, but this is incompitable with the older gtk1.2-series. Therefore it complains. So what you need to get is not "some gtk package", but gtk+1.2-something.

Good luck.

---

### Post by ow50 on 2005-11-18
I'd like to add that assuming your output is from ./configure and you're installing something from source, you'll need the dev package, which is this case is probably libgtk1.2-dev.

---

### Post by ralph4100 on 2005-11-18
thanks, apt-get install libgtk1.2-dev worked. sorry about my confusing way of asking the question, i'm brand new...

---

