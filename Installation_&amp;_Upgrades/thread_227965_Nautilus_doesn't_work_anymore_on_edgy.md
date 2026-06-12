---
title: "Nautilus doesn't work anymore on edgy"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by metnik on 2006-08-02
I upgrated to Edgy and nautilus doesn't work anymore, any ideas?

the package is correctly install even if nautilus --version gives 2.14

```
$ killall nautilus && nautilus

(nautilus:5670): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(nautilus:5670): Gdk-WARNING **: locale not supported by C library
Initializing nautilus-open-terminal extension
Initializing nautilus-image-converter extension
seahorse nautilus module initialized
sys:1: GtkWarning: Self Mount Volume: missing action
sys:1: GtkWarning: Self Unmount Volume: missing action
sys:1: GtkWarning: Self Eject Volume: missing action
sys:1: GtkWarning: Self Format Volume: missing action
sys:1: GtkWarning: find_menu_position: assertion `GTK_IS_WIDGET (prev_child)' failed

(gnome_segv2:5690): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gnome_segv2:5690): Gdk-WARNING **: locale not supported by C library
```

---

### Post by mlind on 2006-08-02
Edgy is under heavy development and some packages are probably pretty much broken. You should post this to Edgy forums instead.

---

### Post by metnik on 2006-08-02
sorry I didn't see that forum

---

