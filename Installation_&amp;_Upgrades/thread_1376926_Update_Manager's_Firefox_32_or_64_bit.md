---
title: "Update Manager's Firefox: 32 or 64 bit?"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2010-01-09
Update Manager wants me to update to Firefox 3.5.7. 

I'm currently running 64-bit Firefox 3.5.6.

I'd like to update, but Update Manager says nothing about this 3.5.7 being the 64-bit version. 

If I upgrade from the UM, I don't know if I'll be getting 32-bit or 64-bit FF.

How can I tell beforehand which one I'll get?

---

### Post by SuperSonic4 on 2010-01-09
It will be 64-bit, especially if it doesn't want to install 32 bit deps

If you want you can always check your package manager but it will be 64 bitr

---

### Post by hansdown on 2010-01-09
Hi watchpocket.

If you are running 64bit, the update should be for 64bit.

---

### Post by watchpocket on 2010-01-09
Thanks, I got 64-bit FF 3.5.7 installed but I appear to have a bit of an upgrade problem with FF:

When I click on the FF icon in the top panel, I get a "Could not launch application . . .  permission denied"

In /usr/bin/ I have: ```

   0 lrwxrwxrwx  1 root   root          34 2009-12-27 17:37 firefox -> /usr/lib/firefox-3.5.6/firefox-3.5
   0 lrwxrwxrwx  1 root   root          31 2010-01-09 18:12 firefox-3.5 -> ../lib/firefox-3.5.7/firefox.sh*
   0 lrwxrwxrwx  1 root   root          11 2009-12-25 03:55 firefox.ubuntu -> firefox-3.5*
```(The top line's gotta go, not exactly sure how to change it / what to change it to.)  
 
I launched FF with "firefox-3.5" in Terminal.  Though it launched, I got a bunch of error messages (here are some of them):

```
zsh  529 --> firefox-3.5                                                       
(firefox:2071): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:2071): GLib-WARNING **: g_set_prgname() called multiple times
LoadPlugin: failed to initialize shared library /home/rj/.mozilla/plugins/nppdf.so [/home/rj/.mozilla/plugins/nppdf.so: wrong ELF class: ELFCLASS32]

(firefox:2071): Gtk-CRITICAL **: gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(firefox:2071): Gtk-CRITICAL **: gtk_text_buffer_get_iter_at_mark: assertion `GTK_IS_TEXT_MARK (mark)' failed

(firefox:2071): Gtk-CRITICAL **: _gtk_text_layout_get_block_cursor: assertion `layout != NULL' failed

(firefox:2071): Gtk-CRITICAL **: gtk_text_layout_get_cursor_locations: assertion `layout != NULL' failed

(firefox:2071): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `GDK_IS_WINDOW (window)' failed

(firefox:2071): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `GDK_IS_WINDOW (window)' failed

(firefox:2071): Gtk-CRITICAL **: gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed
```etc.  How can I fix this so it doesn't happen on future FF upgrades?

---

### Post by watchpocket on 2010-01-11
anyone?

---

