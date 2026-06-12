---
title: "howto read documentaiton installed?"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by kroiz on 2007-07-02
Under the Documentation section in Synaptic there is a long list of stuff.
I thought that those are items that if installed would be used by man but it seems not, cause man works w/o them.
sooo what is it. how do I read this documents once installed if not by man?

---

### Post by cdiem on 2007-07-02
I think you can read any document through "gksudo gedit /Path/to/the/document/Document" in a terminal, if this is what you want to do. For instance, if you have the man page program.txt in /usr/share/doc, then "gksudo gedit /usr/share/doc/program.txt" would open it in the text redactor; you can use oowriter instead of gedit, if you want them to be read in the open office writer program. The gksudo part would give you any rights you need to read a file (and save it); it's just in case you need these rights.

---

### Post by kroiz on 2007-07-03
Thanks cdiem, that is good to know. (-:
just a small correction, after installing several items, browsing that directory showed me that not all documentation are text file some are HTML (make) and some have also PDF version (bash).
Also I think there is no need to use gksudo, read permission suffice.

---

