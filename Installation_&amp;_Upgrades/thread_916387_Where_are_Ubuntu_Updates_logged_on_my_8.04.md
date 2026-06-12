---
title: "Where are Ubuntu Updates logged on my 8.04?"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by grikdog on 2008-09-10
I would like to see what updates have been installed on my system.  I've been merrily allowing Hardy to do its thing.  Now I want to know what it's been up to.  Where should I look to discover update history on my boxen?

Where should I look on the web to find what updates have been offered and whether I received them?

Names? Urls?

Thanks!
d

---

### Post by Partyboi2 on 2008-09-10
you could look at /var/log/apt/term.log

---

### Post by frankleeee on 2008-09-10
Synaptic history as well.

---

### Post by grikdog on 2008-09-10
> **frankleeee said:**
> Synaptic history as well.

Which is located...?  /var/log/synaptic does not exist

---

### Post by frankleeee on 2008-09-10
> **grikdog said:**
> Which is located...?  /var/log/synaptic does not exist

system-administration-synaptic-history.

---

### Post by grikdog on 2009-05-18
Thanks!

System &rarr; Administration &rarr; Synaptic Package Manager &rarr; File &rarr; History  does the trick.

---

