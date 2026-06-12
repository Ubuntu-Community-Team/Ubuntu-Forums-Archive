---
title: "Ldap Client works but no GUI appears"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by SManki on 2012-05-25
I have about 60 Client with Ubuntu 10.04 as ldap client and it works perfect, its Ldap + autofs.
Since Version >10.04 the Ldap Login still works, but no GUI appears (not Gnome-shell, not unity etc).
Ldap Verification works:
getent passwd/group ok
su user ok
ssh login ok
Ldap Server says ok

After waiting to 12.04 there is still no progress to that problem. I found some Forums with the same Problem. It looks like, that the change to upstart (maybe not in 10.04) is the Problem, and that the nscd Server starts bevor dbus Server.
Now Playing around with upstart.
Has anybody out there the same problem and can deliver a solution?
I WONT fall back to Windows, but what can I do?

Any help would be great!

Here is the last .xsession-errors 
```

(gnome-settings-daemon:11288): libupower-glib-WARNING **: Couldn't connect to system bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
gnome-session[11234]: WARNING: Application 'gnome-settings-daemon.desktop' killed by signal

** (nm-applet:11517): WARNING **: Couldn't connect to system bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (nm-applet:11517): CRITICAL **: nm_client_get_state: assertion `NM_IS_CLIENT (client)' failed

** (nm-applet:11517): CRITICAL **: nm_client_networking_get_enabled: assertion `NM_IS_CLIENT (client)' failed

** (nm-applet:11517): CRITICAL **: nm_client_wireless_get_enabled: assertion `NM_IS_CLIENT (client)' failed

** (nm-applet:11517): CRITICAL **: nm_client_wireless_hardware_get_enabled: assertion `NM_IS_CLIENT (client)' failed

** (nm-applet:11517): CRITICAL **: nm_client_wwan_get_enabled: assertion `NM_IS_CLIENT (client)' failed

** (nm-applet:11517): CRITICAL **: nm_client_wwan_hardware_get_enabled: assertion `NM_IS_CLIENT (client)' failed

** (nm-applet:11517): CRITICAL **: nm_client_wimax_get_enabled: assertion `NM_IS_CLIENT (client)' failed

** (nm-applet:11517): CRITICAL **: nm_client_wimax_hardware_get_enabled: assertion `NM_IS_CLIENT (client)' failed

** (nm-applet:11517): CRITICAL **: nm_client_get_devices: assertion `NM_IS_CLIENT (client)' failed

** (nm-applet:11517): WARNING **: Failed to initialize D-Bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(gnome-shell:11505): libupower-glib-WARNING **: Couldn't connect to system bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
    JS ERROR: !!!   Exception was: Error: Error invoking Gio.bus_get_sync: Alle verfügbaren Legitimierungsmechanismen sind ausgeschöpft (EXTERNAL, DBUS_COOKIE_SHA1, ANONYMOUS Versuche) (verfügbar: EXTERNAL, DBUS_COOKIE_SHA1, ANONYMOUS)
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Error invoking Gio.bus_get_sync: Alle verf\xFCgbaren Legitimierungsmechanismen sind ausgesch\xF6pft (EXTERNAL, DBUS_COOKIE_SHA1, ANONYMOUS Versuche) (verf\xFCgbar: EXTERNAL, DBUS_COOKIE_SHA1, ANONYMOUS)")@gjs_throw:0
()@/usr/share/gjs-1.0/overrides/Gio.js:341
ConsoleKitManager()@/usr/share/gnome-shell/js/ui/automountManager.js:40
()@/usr/share/gnome-shell/js/ui/automountManager.js:84
wrapper()@/usr/share/gjs-1.0/lang.js:204
()@/usr/share/gjs-1.0/lang.js:145
()@/usr/share/gjs-1.0/lang.js:239
_createUserSession()@/usr/share/gnome-shell/js/ui/main.js:85
start()@/usr/share/gnome-shell/js/ui/main.js:225
@<main>:1
"'
    JS ERROR: !!!     message = '"Error invoking Gio.bus_get_sync: Alle verfügbaren Legitimierungsmechanismen sind ausgeschöpft (EXTERNAL, DBUS_COOKIE_SHA1, ANONYMOUS Versuche) (verfügbar: EXTERNAL, DBUS_COOKIE_SHA1, ANONYMOUS)"'
Fensterverwalter-Warnung:Log level 32: Execution of main.js threw exception: Error: Error invoking Gio.bus_get_sync: Alle verfügbaren Legitimierungsmechanismen sind ausgeschöpft (EXTERNAL, DBUS_COOKIE_SHA1, ANONYMOUS Versuche) (verfügbar: EXTERNAL, DBUS_COOKIE_SHA1, ANONYMOUS)

** (nautilus:11516): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:11516): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:11516): WARNING **: Can not get _NET_WORKAREA

** (nautilus:11516): WARNING **: Can not determine workarea, guessing at layout
Nautilus-Share-Message: Called "net usershare info" but it failed: »net usershare« gab den Fehler 255 zurück: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Datei oder Verzeichnis nicht gefunden
Please ask your system administrator to enable user sharing.

Verbindungsfehler: Verbindung verweigert
pa_context_new() fehlgeschlagen: Verbindung verweigert

(gdu-notification-daemon:11583): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
======================================================================
Error constructing GduPool: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

This error suggests there's a problem with your udisks or D-Bus installation.
======================================================================

(gdu-notification-daemon:11583): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gdu-notification-daemon:11583): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gdu-notification-daemon:11583): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gdu-notification-daemon:11583): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gdu-notification-daemon:11583): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gdu-notification-daemon:11583): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gdu-notification-daemon:11583): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gdu-notification-daemon:11583): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
**
libgdu:ERROR:gdu-pool.c:2464:gdu_pool_get_devices: assertion failed: (pool != NULL)

(update-notifier:11627): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
======================================================================
Error constructing GduPool: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

This error suggests there's a problem with your udisks or D-Bus installation.
======================================================================

** (update-notifier:11627): WARNING **: initializing gdu failed
WARNING:root:timeout reached, exiting
Error connecting to ConsoleKit: Alle verfügbaren Legitimierungsmechanismen sind ausgeschöpft

```

---

### Post by SManki on 2012-05-30
Have tested with some upstart scripts, not working up to now.
Anybody out there solved the problem??):P

---

### Post by SManki on 2012-06-14
Solved the Problem.
Some guys told me, that the Problem is in the upstart process with dbus and nscd server.
Tested around a lot and found out: The error was in the ldap.conf.
Used in old versions:

# The distinguished name to bind to the server with
# if the effective user ID is root. Password is
# stored in /etc/ldap.secret (mode 600)
rootbinddn cn=admin,o=goofy,c=at

But i had to use 
# The distinguished name to bind to the server with.
# Optional: default is to bind anonymously.
binddn cn=admin,o=goofy,c=at

# The credentials to bind with. 
# Optional: default is no credential.
bindpw ****

Thougt right up to know, that either use rootdn or binddn !? Maybe I will read th eman pages again.

Now the login works out of the Box.

---

