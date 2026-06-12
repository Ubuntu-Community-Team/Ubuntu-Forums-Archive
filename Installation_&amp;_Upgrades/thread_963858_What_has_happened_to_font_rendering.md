---
title: "What has happened to font rendering?"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Fdooch on 2008-10-30
After upgrade to 8.10 fonts look ugly... Cant tell what exactly has happened, but the size and rendering of fonts seems different. And because I liked the way it was before I'd say now it is just wrong... This affects apps and web pages as well

---

### Post by Technoviking on 2008-10-30
Rename the following file to fonts.conf and copy it to /etc/fonts and restart X.

---

### Post by Fdooch on 2008-10-30
Could you explain what has changed with font rendering and what happens when I overwrite the file?

---

### Post by Technoviking on 2008-10-30
If you are nervous back up your old /etc/fonts.conf (should always do that anyways).

---

### Post by Fdooch on 2008-10-30
I played with hinting in font rendering and it seems to help... Is there some insane value in "slight hinting" preset? Now everything looks better, but still looks sharper than it was... Guess that is because of hinting...

---

### Post by mohbana on 2008-11-01
> **Fdooch said:**
> Could you explain what has changed with font rendering and what happens when I overwrite the file?

**Could you explain what has changed with font rendering**

---

