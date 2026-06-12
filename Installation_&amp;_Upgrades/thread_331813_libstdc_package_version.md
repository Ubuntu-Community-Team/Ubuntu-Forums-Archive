---
title: "libstdc package version"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by useResa on 2007-01-05
Hi,

I am trying to install software that I need for my work.
When trying to install this I get the following error
> libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directoryWhen I do *locate libstdc++-libc6* the result is
> /usr/lib/libstdc++-libc6.2-2.so.3My guess is that the software I am trying to run is making use of on older version than installed with Edgy.

My questions:
1. Is there a way that I can install the older version?
2. Maybe even more important: What risks do I take if I should install an older version?

Regards.

[color=red]EDIT:[/color]
For now I have resolved the issue by doing the following in the /urs/lib directory
```
sudo ln -s libstdc++-libc6.2-2.so.3 libstdc++-libc6.1-1.so.2
```

Nevertheless, could someone still answer my questions?

---

### Post by bapoumba on 2007-01-05
Hi,
not sure I can answer your question. But which kind of application were you trying to install and how (some third party repos, a .deb, other) ?

---

### Post by useResa on 2007-01-05
> **bapoumba said:**
> Hi,
not sure I can answer your question. But which kind of application were you trying to install and how (some third party repos, a .deb, other) ?
I was trying to install [SAS software](http://www.sas.com).
The way I have to do it is to run a setup.sh program.

---

