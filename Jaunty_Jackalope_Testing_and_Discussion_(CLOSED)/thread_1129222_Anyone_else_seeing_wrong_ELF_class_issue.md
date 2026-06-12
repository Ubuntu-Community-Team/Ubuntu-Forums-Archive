---
title: "Anyone else seeing wrong ELF class issue"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ktp on 2009-04-18
Ever since yesterdays update, I think it was the ia32-libs, I am getting following when running 32-bit application.  This seems to break the themes in the app.

```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so: wrong ELF class: ELFCLASS64

Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64

Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64
```

---

### Post by trot2millah on 2009-04-18
Is this occurring when you are running a 32-bit app on a 64-bit computer?  Because I have been experiencing the same problem.

---

### Post by ktp on 2009-04-18
Yes.  I have added comments to following bug, which seemed to have updated the ia32-libs yesterday.

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/360870](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/360870)

**Edit**
I have reopened following bug which seemed more likely.  Can you go comment that you are seeing it too.

[https://bugs.launchpad.net/ubuntu/jaunty/+source/ia32-libs/+bug/362939](https://bugs.launchpad.net/ubuntu/jaunty/+source/ia32-libs/+bug/362939)

---

### Post by nystire on 2009-04-18
Seeing it often. :(

---

### Post by FuturePilot on 2009-04-18
Same here.

---

