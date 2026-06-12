---
title: "Firefox emacs key bindings....how now?"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by bodhidharma on 2006-07-29
Hi y'all,

I just upgraded to Dapper (the simple upgrade didn't work as
advertised, but maybe I messed something up; anyway, I had
a recent personal backup -- don't we all before upgrading? --
and just did a fresh install and reloaded my personal files),
and now I cannot figure out how to get Emacs key bindings in
Firefox.  In particular, the standard things people seem to do,
as described in MozillaZine, like gconf-editor and various
.gtkrc files (I've tried .gtkrc-2.0, .gtkrc.mine, .gtkrc-1.2)
all have no effect, I'm stuck with horrific key bindings!

Please help!  Is there something that supercedes these standard
places to change keybindings?

Thanks!

---

### Post by teledyn on 2007-10-19
I second this request.  It is very annoying.  I have set 
```
gtk-key-theme-name = "Emacs"
```
in .gtkrc.mine, but to no effect -- I have emacs bindings in all the terminals and other X apps (including emacs ;) but when I go into Firefox, suddenly the ground shifts and it is not only annoying, it is dangerous.

This worked fine in Mandriva 2007.1, so it's not the fault of the gnome desktop, it is something that Ubuntu has layered on top, or trimmed out.

---

### Post by Sam Rodgers on 2008-02-04
Try entering the following into ~/.gtkrc.mine :

```
include "/usr/share/themes/Emacs/gtk-2.0-key/gtkrc"
```

Assuming that the real .gtkrc files have an include line for ~/.gtkrc.mine , this should load the Emacs bindings.  Restarting the applications is necessary after this change is made.

---

