---
title: "blank dialogue box in netbeans"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by mrityunjay on 2008-08-23
I'm facing a strange problem with netbeans.
whenever i launch it with my user account it displays the following in terminal:
(<unknown>:10539): Gtk-WARNING **: Attempting to add a widget with type GtkButton to a GtkComboBoxEntry (need an instance of GtkEntry or of a subclass)

(<unknown>:10539): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:10539): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed


and sometimes it also displays a blank dialogue box.

but it runs perfectly if i execute it with 'sudo'.
 
can anybody tell me how can I get rid of this problem?
thanks

---

### Post by Partyboi2 on 2008-08-23
Reading [[COLOR=Blue]this[/COLOR]]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6624717"), indicates there is a bug with java and that it is in the process of getting fixed.

---

