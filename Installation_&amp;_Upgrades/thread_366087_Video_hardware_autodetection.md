---
title: "Video hardware autodetection"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by Strom Carlson on 2007-02-20
What is the process that the Ubuntu 6.10 desktop installation CD uses to autodetect video hardware and autogenerate the xorg.conf file, and is it possible to manually invoke this *exact same process* on an already-installed system?  (no, it's not 'sudo dpkg-reconfigure xorg.conf' - I need this to be completely automated)

I've been googling, grepping, editing, and reloading for hours now and I can't find an answer. :/

---

### Post by veloce on 2007-02-21
> **Strom Carlson said:**
> What is the process that the Ubuntu 6.10 desktop installation CD uses to autodetect video hardware and autogenerate the xorg.conf file, and is it possible to manually invoke this *exact same process* on an already-installed system?  (no, it's not 'sudo dpkg-reconfigure xorg.conf' - I need this to be completely automated)

I've been googling, grepping, editing, and reloading for hours now and I can't find an answer. :/

Why don't you include "dpkg-reconfigure xorg.conf" in your init?

---

