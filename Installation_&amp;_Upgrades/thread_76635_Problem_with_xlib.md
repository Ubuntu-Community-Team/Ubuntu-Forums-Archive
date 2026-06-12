---
title: "Problem with xlib"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by jsmidt on 2005-10-15
When I try to edit my sources.list file like this:
```
 gedit /etc/apt/sources.list
```
 
    I get this error message:
```

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gedit:12746): Gtk-WARNING **: cannot open display:

```
    
  Does anybody know what the problem is, and how to fix it?

---

### Post by Qubecnunn on 2005-10-22
Im having same problem with gedit in gnome works fine as normal user but not as su

---

### Post by Qubecnunn on 2005-10-22
found the answer here [http://www.ubuntuforums.org/showthread.php?t=43859&highlight=Gtk-WARNING+gedit](http://www.ubuntuforums.org/showthread.php?t=43859&highlight=Gtk-WARNING+gedit)

 gksudo gedit /etc/whatever

works for me thanks poofyhairguy

---

