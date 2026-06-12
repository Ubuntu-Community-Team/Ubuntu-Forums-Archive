---
title: "auto generate a kernel"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by A_deeper_blue on 2005-02-24
since ubuntu loads up every module possible

is there a way to automatically generate a new (2.6.*) kernel by looking at the modules currently active
(I don't just want to copy the config file)
and not have to load every module under the sun every time you boot up
:P
that could be fun

---

### Post by alastair on 2005-02-24
Modules should only be loaded if you have a device/setup that needs them.

- lsmod

What modules do you have loaded that you don't want?

---

