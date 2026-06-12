---
title: "problem in latest firefox update"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by supereater14 on 2010-09-20
after the latest firefox update, whenever i have a proxy set up, i can't get online. every page says:

XML Parsing Error: undefined entity
Location: jar:file:///usr/lib/firefox-3.6.9/chrome/toolkit.jar!/content/global/netError.xhtml
Line Number 60, Column 12:

what does it mean?

---

### Post by digitalramble on 2010-09-21
Can't help you here, but I'm seeing the same kind of thing.  Not sure if it's a proxy thing -- I'm getting it at random from various different sites, some of them plain public ones, and others that are password protected.  (But I can see other public sites, and other password protected sites, I'm not yet seeing a pattern.).

---

### Post by lovinglinux on 2010-09-21
Looks like you need to re-install Firefox.

Try this:

```
sudo apt-get install --reinstall firefox
```

---

