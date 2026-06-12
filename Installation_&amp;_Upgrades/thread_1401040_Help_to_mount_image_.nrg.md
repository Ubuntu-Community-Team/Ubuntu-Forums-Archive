---
title: "Help to mount image .nrg"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by Locaj on 2010-02-07
Hi

Got cd image I have to load. I tried with Furius. Image format is .nrg and it was done by me in windows xp.

When I run furius from terminal i get message:
```
locaj@locaj-desktop:~$ furiusisomount 
init: wrong standard identifier in volume descriptor 0, skipping..
init: wrong standard identifier in volume descriptor 1, skipping..
init: wrong standard identifier in volume descriptor 2, skipping..
Traceback (most recent call last):
  File "/usr/share/furiusisomount/main.py", line 318, in treeview_mounted_images_cursor_changed
    self.interface.get_widget('label_selected_mount_point').set_label(self.model.get_value(self.iter, 0))
TypeError: iter must be a GtkTreeIter

(nautilus:4200): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

```volume goes up to 17.

Im new to Ubuntu at all (i use 9.10). I dont know is data from cd image suppose to be shown in mnt folder? Be visible from Places?

Thanks

---

### Post by zvacet on 2010-02-07
Read [this.]("https://help.ubuntu.com/community/ManageDiscImages")

---

