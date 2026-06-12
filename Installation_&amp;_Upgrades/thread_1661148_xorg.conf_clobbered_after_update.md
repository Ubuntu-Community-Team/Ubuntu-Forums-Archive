---
title: "xorg.conf clobbered after update"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by jfbilodeau on 2011-01-06
Good day,

I'm using a custom /etc/X11/xorg.conf file. This file gets clobbered every time a update occurs.

Is there anyway for me to tell APT not to touch my xorg.conf?

Thanks!

---

### Post by Zorael on 2011-01-06
Weird; I've never had this happen to me. How do you apply updates?

If you do it via a terminal and it senses that it's about to overwrite a configuration file that you've changed, it will spawn a prompt and ask what you want to do. Overwrite, keep the current file, view the changes side-by-side, etc.

---

