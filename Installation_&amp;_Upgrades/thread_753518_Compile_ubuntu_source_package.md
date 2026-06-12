---
title: "Compile ubuntu source package"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by hissyfut on 2008-04-12
What is the command(s) for compiling an ubuntu source package?

This is assuming all necessary dependency are installed, and all
of the ubuntu source files are in the same directory.
for instance-
program_1.1.orig.tar.gz
program_1.1-2.dsc
program_1.1-2.diff.gz

---

### Post by Pumalite on 2008-04-12
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by hissyfut on 2008-04-12
> **Pumalite said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

This does not answer how to build an ubuntu source package
with a .dsc and patch files

Thanks for the link anyhow

---

### Post by hissyfut on 2008-04-12
anyone?  bump

---

### Post by dmizer on 2008-04-24
rather than flat installing it from source, try actually building a debian package that you can install (and even better: remove) via synaptic.

check here: [http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003) i've used this guide several times before and it's always worked.

---

### Post by hissyfut on 2008-04-26
> **dmizer said:**
> rather than flat installing it from source, try actually building a debian package that you can install (and even better: remove) via synaptic.

check here: [http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003) i've used this guide several times before and it's always worked.

SIGH!! and GRRR!!

dmizer, I appreciate your help, really, BUT,
your answer does not answer the original question.

"What is the command(s) for compiling an ubuntu source package?"

If an ubuntu source package is compiled, using the commands to
"compile an ubuntu source package", then it should be assumed
that the result would be a deb package.

Does anybody read the question to be answered?????

Let me re-phrase,
You want to recompile and create a ubuntu deb package from
an ubuntu source package using the source files from
packages.ubuntu.com (as example in the first post).

So I ask again...

"What is the command(s) for compiling an ubuntu source package?"

---

### Post by hissyfut on 2008-04-29
bump

---

### Post by dmizer on 2008-04-30
> **hissyfut said:**
> SIGH!! and GRRR!!
sorry to have offended you.

the link i posted is entitled "Howto make debian standard debs from scratch".  since "debian standard debs" is the type of package used in ubuntu, following the howto i linked will result in a <your-package>.deb which can subsequently be installed in ubuntu.

have a nice day.

---

