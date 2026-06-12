---
title: "[SOLVED] Specifying a Local Mirror for Upgrades?"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by vertigo23 on 2008-11-03
I have set up a local mirror of Intrepid for my company, using the excellent apt-mirror tool.  Is there a way to get/force update-manager to use this mirror instead of defaulting to us.archive.ubuntu.com?

Thanks!

---

### Post by vertigo23 on 2008-11-19
Solved my own problem - the method detailed here worked great:

[http://www.alandmoore.com/geekpage/index.php?content=92](http://www.alandmoore.com/geekpage/index.php?content=92)

Summary:

Add your local mirror to the appropriate section of /usr/share/python-apt/templates/Ubuntu.mirrors

Select your local mirror in Synaptic (anyone know how to do this without a GUI?)

Upgrade!

---

