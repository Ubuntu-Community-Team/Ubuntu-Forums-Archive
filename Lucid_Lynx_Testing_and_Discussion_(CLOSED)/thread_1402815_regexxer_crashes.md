---
title: "regexxer crashes"
date: 2010-02-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Rallg on 2010-02-09
On Asus EEE 1005HA, using lucid alpha (as of today) upgraded in-place from karmic:

The regexxer search-and-replace software fails in lucid. It previously worked fine in karmic. The failure applies both to to repository pre-complied regexxer, and to compiled-from-source on this machine. Make check shows no errors.

Symptoms: regexxer launches, and locates files. So far, so good. But when I attempt to do a string replace, the program crashes.

When launched from terminal, here are the messages (before the program is asked to to anything):

```
(process:5537): GLib-GObject-WARNING **: cannot register existing type `gtkmm__GtkTextBuffer'
(regexxer:5537): GLib-GObject-WARNING **: cannot register existing type `gtkmm__GtkTextBuffer'
(regexxer:5537): GLib-GObject-WARNING **: cannot retrieve class for invalid (unclassed) type `<invalid>'
(regexxer:5537): GLib-GObject-CRITICAL **: g_object_class_find_property: assertion `G_IS_OBJECT_CLASS (class)' failed
(regexxer:5537): glibmm-WARNING **: Glib::ConstructParams::ConstructParams(): object class "(null)" has no property named "tag_table"
(regexxer:5537): GLib-GObject-CRITICAL **: g_type_class_unref: assertion `g_class != NULL' failed
(regexxer:5537): GLib-GObject-CRITICAL **: g_object_newv: assertion `G_TYPE_IS_OBJECT (object_type)' failed
(regexxer:5537): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
(regexxer:5537): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
(regexxer:5537): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
(regexxer:5537): Gtk-CRITICAL **: gtk_text_buffer_get_iter_at_mark: assertion `GTK_IS_TEXT_MARK (mark)' failed
(regexxer:5537): Gtk-CRITICAL **: gtk_text_layout_get_line_yrange: assertion `_gtk_text_iter_get_btree (iter) == _gtk_text_buffer_get_btree (layout->buffer)' failed
```

Bug report needed, or should I wait? UPDATE: Marked "solved." I reported the bug to launchpad, and was informed that the underlying problem was in a dependent package that is already fixed upstream. At some near future time, routine update will fix this problem.

---

