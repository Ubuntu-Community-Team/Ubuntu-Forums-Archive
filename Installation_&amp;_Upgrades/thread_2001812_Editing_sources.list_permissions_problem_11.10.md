---
title: "Editing sources.list permissions problem 11.10"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by Rotblatt on 2012-06-11
Hey all,
I've been trying to edit my sources.list file in /ect/apt.
I try to use sudo gedit; however, terminal spits back a strange error set that seems related to permissions problems since it will still not let me save the new text file.

Any help on this would be great!
Thanks!

BTW here is the error from terminal:

(gksu:2414): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2414): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2414): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2414): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by drs305 on 2012-06-11
Those messages are an annoyance but shouldn't prevent you from using gedit as root to edit your file:

```
gksu gedit /etc/apt/sources.list &
```

"gksu" is preferred over "sudo" for graphical apps.
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by Rotblatt on 2012-06-11
Yup that worked!
Why was the & necessary, if you don't mind me asking.

---

### Post by drs305 on 2012-06-11
> **Rotblatt said:**
> Yup that worked!
Why was the & necessary, if you don't mind me asking.

It's not necessary, but it frees up the terminal window so you can run other commands if you wish even while gedit is open.

The SOLVED tag is accessed via Thread Tools to the top right of the first post when you feel satisfied with this thread.

---

### Post by Cavsfan on 2012-06-11
```
gksu:2414): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2414): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2414): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2414): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",     
```Drs305, weren't those errors indicative of the problem with using sudo instead of gksu on a graphical application?
Just wondering myself.

---

### Post by drs305 on 2012-06-11
> **Cavsfan said:**
> ```
gksu:2414): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2414): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2414): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2414): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",     
```Drs305, weren't those errors indicative of the problem with using sudo instead of gksu on a graphical application?
Just wondering myself.

Not sure. I don't get the error with either sudo or gksu, to be honest. But I may have tweaked my system - see below. I know I have gotten that error using nautilus on some releases, and I never use "sudo" with graphical apps.

The pixmaps error is a known bug, and the messages can be eliminated by installing *gtk2-engines-pixbuf*.

---

### Post by Cavsfan on 2012-06-11
> **drs305 said:**
> Not sure. I don't get the error with either sudo or gksu, to be honest. But I may have tweaked my system - see below. I know I have gotten that error using nautilus on some releases, and I never use "sudo" with graphical apps.

The pixmaps error is a known bug, and the messages can be eliminated by installing *gtk2-engines-pixbuf*.

Good to know! I installed gtk2-engines-pixbuf just to be safe. For some reason the 32 bit version was already installed (gtk2-engines-pixbuf:i386).
Thanks :)

---

