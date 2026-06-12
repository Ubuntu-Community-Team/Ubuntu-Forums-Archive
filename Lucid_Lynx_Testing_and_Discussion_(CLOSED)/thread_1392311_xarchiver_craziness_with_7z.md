---
title: "xarchiver craziness with 7z"
date: 2010-01-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ibidem on 2010-01-27
I've been using Xarchiver for extraction, and have found some "interesting" behaviors:
1 Access 7z archive on NTFS, it automatically crashes with a core dump (since attempting an update yesterday that failed)
2. Copy same archive to ext4, it opens but names are crazy.  Extracted, the names are good.
3. Close causes a core dump.
I'm wondering if the crash is a library version issue, a botched update, or a preexisting bug in xarchiver. Here's the core dump:

```
ibid@newbook:~/Desktop$ xarchiver

(xarchiver:7287): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/gvfs/gvfs-gdu-volume-monitor received signal 11

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWidget'

(xarchiver:7287): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(xarchiver:7287): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(xarchiver:7287): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xarchiver:7287): Gtk-CRITICAL **: gtk_widget_unrealize: assertion `GTK_IS_WIDGET (widget)' failed

(xarchiver:7287): Gtk-CRITICAL **: gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault (core dumped)

```
The crash occurred when I clicked close.

---

