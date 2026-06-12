---
title: "gnome-panel seems to freeze after login"
date: 2009-07-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kingborel on 2009-07-18
Ok, after Friday's updates gnome-panel freezes on login. The applications menu appears but is unresponsive, and no other applets load (including system tray and f-u-s). I waited a bit to see if another round of updates fixed it, but to no avail. 

Anyone else come across this?

---

### Post by afv on 2009-07-18
If you do use AWN: [http://ubuntuforums.org/showthread.php?t=1210352](http://ubuntuforums.org/showthread.php?t=1210352).

---

### Post by kingborel on 2009-07-18
Nah don't use AWN, just regular gnome-panel. Here's the .xsession-errors log

> /etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: Setup done, will execute: /usr/bin/ssh-agent -- gnome-session
GNOME_KEYRING_SOCKET=/tmp/keyring-B1odlU/socket
SSH_AUTH_SOCK=/tmp/keyring-B1odlU/socket.ssh

(gnome-settings-daemon:4649): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:4649): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:4649): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
gnome-session[4631]: Gtk-WARNING: Unable to locate theme engine in module_path: "pixmap",
Window manager warning: Failed to read saved session file /home/borrell/.config/metacity/sessions/1023331d5971d4c2b2124797363926033100000046310013.ms: Failed to open file '/home/borrell/.config/metacity/sessions/1023331d5971d4c2b2124797363926033100000046310013.ms': No such file or directory
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:4662): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(polkit-gnome-authentication-agent-1:4667): GLib-GIO-WARNING **: g_simple_async_result_complete() called from outside main loop!

(polkit-gnome-authentication-agent-1:4667): GLib-GIO-WARNING **: g_simple_async_result_complete() called from outside main loop!

(polkit-gnome-authentication-agent-1:4667): GLib-GIO-WARNING **: g_simple_async_result_complete() called from outside main loop!

(nautilus:4663): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-power-manager:4668): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(nm-applet:4675): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bluetooth-applet:4673): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
** (nm-applet:4675): DEBUG: applet_common_device_state_changed
** (nm-applet:4675): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:4675): DEBUG: applet_common_device_state_changed

(gnome-panel:4662): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 24
Unable to open desktop file evolution-mail.desktop for panel launcher
gnome-session[4631]: ******************* START ********************************
gnome-session[4631]: Frame 0: gnome-session [0x8060535]
gnome-session[4631]: Frame 1: gnome-session [0x80606d9]
gnome-session[4631]: Frame 2: [0x1b3400]
gnome-session[4631]: Frame 3: /usr/lib/libgobject-2.0.so.0 [0x134a0c]
gnome-session[4631]: Frame 4: /usr/lib/libgobject-2.0.so.0(g_type_check_is_value_type+0x125) [0x138d25]
gnome-session[4631]: Frame 5: /usr/lib/libgobject-2.0.so.0(g_value_init+0x30) [0x13f2b0]
gnome-session[4631]: Frame 6: /usr/lib/libdbus-glib-1.so.2 [0xa8e548]
gnome-session[4631]: Frame 7: /usr/lib/libdbus-glib-1.so.2(dbus_g_proxy_call_with_timeout+0x298) [0xa8e938]
gnome-session[4631]: Frame 8: gnome-session [0x8058fa4]
gnome-session[4631]: Frame 9: gnome-session [0x8067e46]
gnome-session[4631]: Frame 10: gnome-session [0x8069ecf]
gnome-session[4631]: Frame 11: /usr/lib/libdbus-glib-1.so.2 [0xa8b51c]
gnome-session[4631]: Frame 12: /usr/lib/libdbus-glib-1.so.2 [0xa8bd48]
gnome-session[4631]: Frame 13: /lib/libdbus-1.so.3 [0xcf3f33]
gnome-session[4631]: Frame 14: /lib/libdbus-1.so.3(dbus_connection_dispatch+0x3cc) [0xce6d0c]
gnome-session[4631]: Frame 15: /usr/lib/libdbus-glib-1.so.2 [0xa8871d]
gnome-session[4631]: Frame 16: /usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f8) [0x95bbc8]
gnome-session[4631]: Frame 17: /usr/lib/libglib-2.0.so.0 [0x95f470]
gnome-session[4631]: Frame 18: /usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1bf) [0x95f8df]
gnome-session[4631]: Frame 19: /usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0x303c49]
gnome-session[4631]: Frame 20: gnome-session [0x806204b]
gnome-session[4631]: Frame 21: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xe5d7c5]
gnome-session[4631]: Frame 22: gnome-session [0x8050da1]
gnome-session[4631]: ******************* END **********************************

** (nautilus:4663): WARNING **: Unable to add monitor: Not supported
** (nm-applet:4675): DEBUG: applet_common_device_state_changed
** (nm-applet:4675): DEBUG: applet_common_device_state_changed

** (gnome-panel:4662): WARNING **: Could not ask session manager if shut down is available: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (gnome-settings-daemon:4649): WARNING **: No screensaver available


---

### Post by wayne_cat on 2009-07-18
could you please try this

```
sudo apt-get install gtk2-engines-pixbuf
```

---

### Post by chrisccoulson on 2009-07-19
This is because you updated consolekit without updating gnome-session, which exposes a crash in gnome-session when you first log in.

You'll need to update gnome-session from the console to fix it

---

### Post by chrisccoulson on 2009-07-19
FWIW, the bug you're experiencing is related to [https://bugs.edge.launchpad.net/ubuntu/+source/gnome-session/+bug/399531]("https://bugs.edge.launchpad.net/ubuntu/+source/gnome-session/+bug/399531")

In hindsight, I probably should have sent a mail to ubuntu-devel warning people not to upgrade consolekit without upgrading gnome-session

---

### Post by gwenn on 2009-07-19
I removed gnome-panel and ubuntu-desktop and now I'm using cairo-dock which does everything you need, but needs some extra from their website.
Cairo is coool!

---

### Post by chrisccoulson on 2009-07-19
> **gwenn said:**
> I removed gnome-panel and ubuntu-desktop and now I'm using cairo-dock which does everything you need, but needs some extra from their website.
Cairo is coool!

And that won't work for the OP because they don't have a problem with their panel. The fact that their panel doesn't work is just a side-effect of gnome-session crashing, and is not an issue with the panel. The OP will probably find that virtually nothing in their session works.

---

### Post by gwenn on 2009-07-19
Yes , but I had the same problem, nothing in my sesion worked , I only had the dock but I could't do anything so I must do everything from CLI. After removing gnome-panel everything turns normal so now I have a usable box.

---

### Post by kingborel on 2009-07-20
> **wayne_cat said:**
> could you please try this

```
sudo apt-get install gtk2-engines-pixbuf
```

Yeah thanks, the lack of the theme engines is due to my minimal install.

> **chrisccoulson said:**
> This is because you updated consolekit without updating gnome-session, which exposes a crash in gnome-session when you first log in.

You'll need to update gnome-session from the console to fix it

Great, so it's a known problem. The update for gnome-session is showing up in the repos, but it's being kept back. Any way I can find out why?

---

### Post by chrisccoulson on 2009-07-20
There shouldn't be anything keeping it back.

---

### Post by kingborel on 2009-07-20
Thanks, an apt-get dselect-upgrade fixed the problem. All back to normal. Thanks for the help

---

