---
title: "Automatix woes"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by dal2k5 on 2007-11-19
i run 6.06 and i installed automatix properly but when i start it up i get the following error from the terminal > gadri@family:~$ automatix2
Starting
TRAY ICON CREATED
Traceback (most recent call last):
  File "/usr/bin/automatix.py", line 63, in ?
    main = main_ui()
  File "/usr/lib/automatix2/main_interface.py", line 19, in __init__
    self.build_interface()
  File "/usr/lib/automatix2/main_interface.py", line 51, in build_interface
    self.generate_menus()
  File "/usr/lib/automatix2/main_interface.py", line 119, in generate_menus
    self.generate_catalog_model()
  File "/usr/lib/automatix2/main_interface.py", line 362, in generate_catalog_model
    icon= gtk.gdk.pixbuf_new_from_file(list.icon)
gobject.GError: Failed to open file '/usr/share/icons/Tango/24x24/devices/gnome-dev-media-ms.png': No such file or directory
gadri@family:~$

---

### Post by kyphi on 2007-11-20
You may find an answer to your puzzle at this address
[http://www.getautomatix.com/forum/index.php?showforum=32](http://www.getautomatix.com/forum/index.php?showforum=32)

---

### Post by dal2k5 on 2007-11-20
yeah i looked around didnt find anything, and i posted yet to be responded to :(

[http://www.getautomatix.com/forum/index.php?showtopic=1659](http://www.getautomatix.com/forum/index.php?showtopic=1659)

---

### Post by Sef on 2007-11-20
Ubuntu does not support Automatix, and Automatix want you to use their forums to resolve any issues with it.  Since you have provided a link to your thread in Automatix, I will lock this thread to stop any chance of a flame war starting.

---

