---
title: "Many problems after upgrading to 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by manolomanolo on 2011-10-14
Hi to all.

i don't know what appened after upgrading from 11.04 to 11.10 but I experience a lot of problems.
When trying to start the system, it hangs while loading Alsa (pls see attached image).
Then if after I try to load the system in command line by pressing ALT+F3 then I can login and run commands such as:
[LIST]
[*]sudo apt-get update && sudo apt-get upgrade
[*]sudo dpkg --configure -a
[/LIST]

but I still see there are some packages that have not been upgraded.
Even if I run **startx** I enter into Unity which in tourn doesn't seem to work perfectly.

How can I try and solve my problems?
I will attach a dmesg soon.

Thanks.
Regards.

---

### Post by manolomanolo on 2011-10-14
Pls still wait for the picture and the dmesg. In fact, at the moment I am trying to remove Ubity and install Gnome to see what it happens.

At the moment I can also add that nautilus doesn't work anymore.
```
nautilus
Gtk-Message: Failed to load module "canberra-gtk-module"
** (nautilus:3169): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object
Initializing nautilus-open-terminal extension
`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)


(nautilus:3169): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

(nautilus:3169): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed
`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': nautilus: undefined symbol: menu_proxy_module_load

(nautilus:3169): Gtk-WARNING **: Failed to load type module: (null)

**Errore di segmentazione** (*that is **SEGMENTATION FAULT***)

```

---

### Post by michael111 on 2011-10-14
The Nautilus seg fault is also affecting me

```

mic@mic:~$ nautilus
Initializing nautilus-gdu extension
** (nautilus:2370): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-open-terminal extension

(nautilus:2370): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

(nautilus:2370): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:2370): GConf-CRITICAL **: gconf_client_get: assertion `GCONF_IS_CLIENT (client)' failed

(nautilus:2370): GConf-CRITICAL **: gconf_client_get: assertion `GCONF_IS_CLIENT (client)' failed

(nautilus:2370): GConf-CRITICAL **: gconf_client_get: assertion `GCONF_IS_CLIENT (client)' failed
Segmentation fault

```

All I did was navigate to some folders.

---

### Post by manolomanolo on 2011-10-14
Here it is my dmesg and the picture of the possible Alsa failure in attachment.

---

### Post by manolomanolo on 2011-10-15
I could imagine the problem affects the whole system.
Till now, I discovered that both Nautilus and Synaptic go in **SEGMENTATION FAULT**
Any clue?
Thanks

---

### Post by manolomanolo on 2011-10-16
up

---

### Post by manolomanolo on 2011-10-18
Still no solutions?

---

### Post by atentik on 2011-10-18
This was what I did when I had the same problem. I believe the problem is with lightdm.
When you get stack, try this:
1. Press Ctr+Alt+F1 then
2. > sudo gdm, this should boot you to the gnome graphic and you should be able to log on. Your 3d graphic will not work when you do this but it will allow you to log on. Plus, your computer will be very slow.
3. Now, you can change the default *dm to gdm. Here is how:
```
sudo gedit /etc/X11/default-display-manager
```. At the line, change the last thing to ..../gdm instead of lightdm.

---

### Post by alphacrucis2 on 2011-10-18
> **manolomanolo said:**
> Still no solutions?


On the nautilus issue. Try removing natilus-open-terminal plugin if you have it and see if that helps the nautilus problem. I recall there was a bug with it that caused nautilus to segfault. Not sure if it is fixed at this point.

---

### Post by manolomanolo on 2011-10-19
> **atentik said:**
> This was what I did when I had the same problem. I believe the problem is with lightdm.
When you get stack, try this:
1. Press Ctr+Alt+F1 then
2. , this should boot you to the gnome graphic and you should be able to log on. Your 3d graphic will not work when you do this but it will allow you to log on. Plus, your computer will be very slow.
3. Now, you can change the default *dm to gdm. Here is how:
```
sudo gedit /etc/X11/default-display-manager
```. At the line, change the last thing to ..../gdm instead of lightdm.

Unfortunately I got some problems in trying to following your suggestion. First of all, pressing Ctr+Alt+F1 has the same effects than pressing ALT+F1. Second, running **gdm** gives the following errors:
```
** (gdm-binary:2056): WARNING **: Failed to adquire org.gnome.DisplayManager: Connection ":1.19" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:2056): Could not acquire name; bailing out
```

Instead, when trying to run **sudo gdm** the terminal gets stucked after giving the following error:
```
gdm-binary[2081]: WARNING: GdmDisplay: display lasted 0,336252 seconds
```

Now, what should I do? Taking into account that I can do run into graphic mode by executing **startx**, should I gedit that file after loading startx?

---

### Post by manolomanolo on 2011-10-19
Swapping lightdm with gdm did not solve the problem

---

