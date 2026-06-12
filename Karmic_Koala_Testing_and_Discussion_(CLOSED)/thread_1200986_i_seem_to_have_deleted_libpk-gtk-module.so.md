---
title: "i seem to have deleted libpk-gtk-module.so"
date: 2009-06-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-06-30
how do i find out which package owns  libpk-gtk-module.so?

i get this in my auth.log
```
Jun 30 23:18:19 puccaso-mini gnome-keyring-ask: Gtk: Failed to load module "pk-gtk-module": libpk-gtk-module.so: cannot open shared object file: No such file or directory

```

any ideas?

---

### Post by ronacc on 2009-06-30
I'm getting that also , seems to have been taken out by an update . Just wait it will straighten itself out .

---

### Post by dinxter on 2009-06-30
dont think the packagekit gtk module is in the repos at the mo but it can be disabled if need be, see [https://bugs.launchpad.net/ubuntu/+source/packagekit-gnome/+bug/389766](https://bugs.launchpad.net/ubuntu/+source/packagekit-gnome/+bug/389766)

---

