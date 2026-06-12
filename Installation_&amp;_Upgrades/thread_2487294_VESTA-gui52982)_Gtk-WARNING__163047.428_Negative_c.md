---
title: "VESTA-gui:52982): Gtk-WARNING **: 16:30:47.428: Negative content width -2"
date: 2023-05-30
forum: Installation &amp; Upgrades
---

### Post by sumakhoo on 2023-05-30
Hi I am using Ubuntu 22.04.2 LTS.
I download the VESTA-gtk3.tar.bz2.
and I put the VESTA path in my .bashrc file export PATH=$PATH:/home/cmc/software/VESTA-gtk3
I also install the libgtk by
$ sudo apt install libgtk-4-dev

But I am getting the following error although VESTA is working.

```

$ VESTA

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.428: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.428: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.428: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.428: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-CRITICAL **: 16:30:47.429: gtk_box_gadget_distribute: assertion 'size >= 0' failed in GtkNotebook

(VESTA-gui:52982): Gtk-CRITICAL **: 16:30:47.444: gtk_box_gadget_distribute: assertion 'size >= 0' failed in GtkNotebook

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.502: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.502: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-CRITICAL **: 16:30:47.502: gtk_box_gadget_distribute: assertion 'size >= 0' failed in GtkNotebook

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.524: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.524: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.541: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.541: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.558: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.558: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.575: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.575: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.591: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.591: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)

(VESTA-gui:52982): Gtk-WARNING **: 16:30:47.607: Negative content width -2 (allocation 32, extents 17x17) while allocating gadget (node button, owner GtkButton)
```

Please help me to run it properly.
Thank You

---

### Post by MAFoElffen on 2023-05-31
> **sumakhoo said:**
> Hi I am using Ubuntu [COLOR=#ff0000]22.04.2 LTS[/COLOR].
From: [https://www.ch.cam.ac.uk/computing/managed-linux-workstations](https://www.ch.cam.ac.uk/computing/managed-linux-workstations)
> The latest version of the image is based on [COLOR=#ff0000]Ubuntu 20.04 (Focal Fossa)[/COLOR].

---

