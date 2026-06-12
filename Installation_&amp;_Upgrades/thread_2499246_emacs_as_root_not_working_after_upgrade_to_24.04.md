---
title: "emacs as root not working after upgrade to 24.04"
date: 2024-07-20
forum: Installation &amp; Upgrades
---

### Post by Giana on 2024-07-20
after the upgrade from 23.10 to 24.04, I cannot launch emacs with sudo any longer.
The error I get is:

```
(emacs:8019): Gtk-WARNING **: 09:16:06.422: Could not load a pixbuf from /org/gtk/libgtk/icons/16x16/status/image-missing.png.
This may indicate that pixbuf loaders or the mime database could not be found.
**
Gtk:ERROR:../../../../gtk/gtkiconhelper.c:494:ensure_surface_for_gicon: assertion failed (error == NULL): Failed to load /org/gtk/libgtk/icons/16x16/status/image-missing.png: Unrecognized image file format (gdk-pixbuf-error-quark, 3)
Bail out! Gtk:ERROR:../../../../gtk/gtkiconhelper.c:494:ensure_surface_for_gicon: assertion failed (error == NULL): Failed to load /org/gtk/libgtk/icons/16x16/status/image-missing.png: Unrecognized image file format (gdk-pixbuf-error-quark, 3)
Fatal error 6: Aborted
```

Googling a bit I've the suspect that it is pixbuf related but the suggestions found online either don't work or don't help.

Any help to debug the issue?

Thanks in advance.

G.

---

### Post by Impavidus on 2024-07-20
Most application are happy to run as root, some aren't, and such things may change from one version of Ubuntu to the next. I don't know about Emacs. For most applications, and that includes emacs, it isn't wise to run them as root. To edit text files with root permission, use the sudoedit command. It copies the file to a temporary location, runs the text editor, waits for the text editor to terminate and copies the edited file back. Use the EDITOR environment variable to choose your text editor and set any options you might need. Default is nano.

---

### Post by currentshaft on 2024-07-21
Friends don't let friends run X applications as root.

---

