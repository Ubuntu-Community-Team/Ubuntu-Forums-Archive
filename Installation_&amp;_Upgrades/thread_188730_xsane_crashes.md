---
title: "xsane crashes"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2006-06-04
I have tried and failed to find documentation on how to set up xsane for my network attached HP printer/scanner. Here is what I know and what results I am getting. I hope someone here can fill-in the missing pieces.

Hardware: HP Photosmart 2600 (printer, scanner, fax), network attached.
The printer setup worked and the printer works (HP "jet direct" setup).

I am trying to use the same scanner setup that worked with Fedora core 5:
command line: 
$ xsane hpaio:/net/Photosmart_2600_series?ip=192.168.178.4

Results:

(xsane:12655): Gtk-CRITICAL **: gtk_accel_label_new: assertion `string != NULL' failed

(xsane:12655): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

(xsane:12655): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_WIDGET (widget)' failed

(xsane:12655): Gtk-CRITICAL **: gtk_accel_label_set_accel_widget: assertion `GTK_IS_ACCEL_LABEL (accel_label)' failed

Segmentation fault

---

### Post by wzzrd on 2006-06-05
Same error here, though with a usb hp psc 2110 connected locally.

---

### Post by wzzrd on 2006-06-08
Found the sollution in a previous thread. Just delete ~/.sane and you're good to go.

---

### Post by kornelix on 2006-06-08
thanks wzzrd, it works.

---

### Post by David Valentine on 2006-06-09
Worked for me, too.  Thanks!

---

### Post by saracen on 2006-12-28
Didn't work for me.  I'm not sure if I have the same error though.  When I open xsane, it detects my psc 2110 but then as soon as I select it and click OK, it just hangs.  No output onto the terminal and no other info.... :confused:

---

