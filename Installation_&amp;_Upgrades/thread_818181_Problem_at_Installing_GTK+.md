---
title: "Problem at Installing GTK+"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by theCoyote on 2008-06-04
hello, i have this problem here

i want to install the gtk+-2.8.20 package.
and as i did the 'make' command, it says:

**gtkiconfactory.c error: conflicting types for 'g_hash_table_get_keys'**

:confused: what should i do now???

---

### Post by dstew on 2008-06-04
See [this thread]("http://ubuntuforums.org/showthread.php?t=645480"). The error might be due to a conflict between GLib and GTK,  some versions of which have the same-named function with different definitions. Make sure you have the newest stable versions of both GLib and GTK+.

---

### Post by theCoyote on 2008-06-04
thanks man :)

how can i send a GRP?

---

### Post by theCoyote on 2008-06-04
i have installed glib successfully :D and now, how do i uninstall the other version of glib?? because as i try to 'make' gtk+, it still reports the same error...

i am using:
- glib 2.6.6
- gtk+ 2.8.20
- pango 1.20.3

---

### Post by dstew on 2008-06-05
If the original source file has an uninstall rule in the makefile, you can just go the the source directory and do```
make uninstall
```It there is no uninstall rule, you can remove the compiled package by hand, by doing **make install** again, and noting the file names and directory locations of the installed files, and deleting them. You might also have to delete a hidden config file in your home directory. See [this thread]("http://www.linuxquestions.org/questions/linux-newbie-8/source-uninstall-with-make-uninstall-howto-230225/"), and [this thread]("http://www.linuxquestions.org/questions/linux-software-2/uninstall-from-src-if-no-make-uninstall-318340/").

By the way, why do you need to install gtk+ 2.8.20? The [stable release]("http://www.gtk.org/download-linux.html") is up to 2.12, and GLib is up to 2.16...

---

