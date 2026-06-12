---
title: "Gnome-App-Installer - crash at search"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by letiro on 2008-03-17
Hello everybody :),

After installation of Ubuntu 7.10 i had the following problem:

When i tried to search for a program in the Gnome-App-Installer (Add/Remove) every time the program crash.


Here is the output of the terminal:

```
$ gnome-app-install

** (gnome-app-install:8097): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1261: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed

(gnome-app-install:8097): GStreamer-CRITICAL **: gst_structure_empty_new: assertion `gst_structure_validate_name (name)' failed
Segmentation fault (core dumped)

```


I've tried to reinstall gnome-app-install and python2.5 but i didn't solve the problem!

I hope any body out there could help me with this problem...

thx
greets letiro

---

### Post by letiro on 2008-03-17
Couldn't solve the problem yet!

Maybe i destroyed the whole system with an external repository!
Right know i'm going to reinstall the system!

Thanks for your help anyway!


greets letiro

---

