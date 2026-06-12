---
title: "Google avant-window-navigator"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by trstn on 2007-02-01
[http://code.google.com/p/avant-window-navigator/](http://code.google.com/p/avant-window-navigator/) 

Anyone else seen this? Looks like a quality OSX style dock but I'm having problems with it.

On install i get (in the terminal)

```
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:

No package 'libwnck-1.0' found
```

But i have libwnck18 installed through synaptic, libwnck-1.0 doesn't seem available anywhere, any ideas?

---

### Post by glabouni on 2007-02-01
I've seen it less than an hour ago on this very forum.
seems it has been features on digg ^^

this is not a google product, but the work of [Neil J. Patel]("http://njpatel.blogspot.com/"), google just host the project.

that said I haven't tried it and can't help you, but you should mention what version you installed rpm, tar.gz or from svn

-edit-
I tried it out of curiosity.
went to the project page, read it, got source from svn compiled it, got the segmentation fault bug, used the advised gconf fix and it worked.

*hint* your problem comes from you not reading the project page download section.

---

### Post by jackhynes on 2007-02-01
@trstn - I have the same problem and can't seem to install libwnck-1.0. Any ideas anyone?

---

### Post by trstn on 2007-02-02
someone made a .deb for it

[http://blog.paulbetts.org/index.php/2007/02/01/avant-window-navigator-for-ubuntu-edgy/#comment-529](http://blog.paulbetts.org/index.php/2007/02/01/avant-window-navigator-for-ubuntu-edgy/#comment-529)

aceness :)

---

