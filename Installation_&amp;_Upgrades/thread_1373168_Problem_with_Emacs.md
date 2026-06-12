---
title: "Problem with Emacs"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by theturbanator on 2010-01-05
Hi everyone,

I recently upgraded to Ubuntu 9.10 from 9.04, and now I am facing a problem with Emacs:

Whenever I run Emacs, it works, but I get the following message:

```
(emacs:2861): GLib-WARNING **: g_set_prgname() called multiple times
```I tried uninstalling and reinstalling Emacs and also deleting the .emacs.d directory (I saw a fix for this problem when trying to run Firefox from the command line that involves simply deleting the .mozilla file). Was it a bad idea to delete the .emacs.d directory? Even after reinstalling Emacs, I do not have that directory any longer. Is it necessary? How can I get it back?

And how can I get this correct this problem?

Thank you very much!

---

### Post by kellemes on 2010-01-05
I had this with Nautilus last week but for some reason it disappeared.
Anyway, you're not the only one..
[https://bugs.launchpad.net/ubuntu/+source/emacs-snapshot/+bug/501670]("https://bugs.launchpad.net/ubuntu/+source/emacs-snapshot/+bug/501670")

---

