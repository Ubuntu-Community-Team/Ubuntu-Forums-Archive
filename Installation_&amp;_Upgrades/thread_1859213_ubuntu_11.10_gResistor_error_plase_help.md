---
title: "ubuntu 11.10 gResistor error plase help"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by qpens on 2011-10-13
[FONT=monospace](gresistor:2547): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gresistor:2547): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gresistor:2547): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gresistor:2547): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Traceback (most recent call last):
  File "/usr/bin/gresistor", line 20, in <module>
    from SimpleGladeApp import SimpleGladeApp
  File "/usr/share/gresistor/SimpleGladeApp.py", line 28, in <module>
    import gtk.glade
ImportError: No module named glade


How can I fix this problem?

[/FONT]

---

### Post by carranty on 2011-10-14
I get a similar problem when running nvidia-settings. Hopefully someone will come to our rescue!

---

### Post by carranty on 2011-10-14
Having looked around online I found a post that recommended you install gtk2-engines-pixbuf.  Open a terminal and type
[I]
sudo apt-get install gtk2-engines-pixbuf

[/I]That solved the problem for me

---

### Post by BobMarleyy on 2011-10-15
> **carranty said:**
> Having looked around online I found a post that recommended you install gtk2-engines-pixbuf.  Open a terminal and type
[I]
sudo apt-get install gtk2-engines-pixbuf

[/I]That solved the problem for me

Thank you for this suggestion. It fixes the Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap"

I want to add to this post that I've seen this gtk-warning for multiple programs.

---

### Post by qpens on 2011-10-16
After sudo apt-get install gtk2-engines-pixbuf


Traceback (most recent call last):
  File "/usr/local/bin/gresistor", line 17, in <module>
    from SimpleGladeApp import SimpleGladeApp
  File "/usr/local/lib/python2.7/dist-packages/SimpleGladeApp.py", line 28, in <module>
    import gtk.glade
ImportError: No module named glade

How to fix that ?

---

### Post by BobMarleyy on 2011-10-19
> **qpens said:**
> After sudo apt-get install gtk2-engines-pixbuf


Traceback (most recent call last):
  File "/usr/local/bin/gresistor", line 17, in <module>
    from SimpleGladeApp import SimpleGladeApp
  File "/usr/local/lib/python2.7/dist-packages/SimpleGladeApp.py", line 28, in <module>
    import gtk.glade
ImportError: No module named glade

How to fix that ?

I am no expert but try installing glade-gtk2
Maybe you also need libglade2-0 and/or python-glade2

---

### Post by qpens on 2011-10-22
glade-gtk2 fix the problem thanks Thanks

---

