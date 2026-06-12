---
title: "Tracking the reason for installing additional packages to ease future removal?"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by davideps on 2013-05-02
Hello,

I had to install some additional packages (postgresql, postGIS, R, etc) on top of lubuntu to recreate my windows work environment. Those packages had perhaps fifty dependencies. Are there any tools that would allow me to annotate what was added when and why? Perhaps later I could go back and uninstall unneeded packages.

thank you,
-david

---

### Post by snowpine on 2013-05-02
Browse /var/log/apt/ for a complete history.

Also "man apt-get" to learn more about "apt-get autoremove" (a command I personally do not use or recommend, but which is very popular). **Always** read the list of packages-about-to-be-removed before answering "y"!! ;)

---

