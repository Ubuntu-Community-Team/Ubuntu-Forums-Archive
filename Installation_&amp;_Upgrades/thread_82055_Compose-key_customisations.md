---
title: "Compose-key customisations"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by cassowary on 2005-10-25
With Ubuntu 5.04, I had some compose key customisations stored in a file at /usr/X11R6/lib/X11/locale/en_AU.UTF-8/Compose (I also had to export the environmental variable GTK_IM_MODULE=xim). Unfortunately, the upgrade to 5.10 deleted that file, as well as all the other related file in its vicinity except for one, which only defines a bunch of Latin-1 compositions (whereas I want things like a-macron from Unicode), and editing this one file (/usr/X11R6/lib/X11/locale/O/Compose) or copying it to the old file and editting it there doesn't seem to do anything. Gtk+ also picks up some unicode characters (like &#331; or ‘) from somewhere, but I can't seem to find it...

Does anyone know how I can customise them under Ubuntu 5.10? Also, is there by any chance a file I can put somewhere into ~ so that next time I upgrade I don't have to worry about them being deleted and the procedure change?

Thanks!

(Just to clarify, my $LANG is set to" en_AU.UTF-8", which is where the first path comes from.)

---

