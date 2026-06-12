---
title: "gnome-logs error messages"
date: 2023-10-14
forum: Installation &amp; Upgrades
---

### Post by diablo2222 on 2023-10-14
Hi,

I just installed gnome-logs (sudo apt install gnome-logs), then started it (sudo gnome-logs), and it starts but I also see two error messages:
> moi@Moi:~$ sudo gnome-logs

(gnome-logs:6358): GLib-GIO-CRITICAL **: 12:12:31.075: g_file_info_get_attribute_boolean: assertion 'G_IS_FILE_INFO (info)' failed


(gnome-logs:6358): GLib-GObject-CRITICAL **: 12:12:31.080: g_object_unref: assertion 'G_IS_OBJECT (object)' failed




Should I do something or it's OK???

---

### Post by deadflowr on 2023-10-14
1) Doesn't need to be run as root (sudo), the error, as far as I see, is specifically because you are trying to run it as root.
A test of running with sudo and without sudo shows me those messages when with sudo and no messages when without sudo.

2) Just press the Super key (or click on the apps menu icon) and type log and it'll be the entry named Logs, select and that's it.
Should also show up inside the menu item Utilities.

---

