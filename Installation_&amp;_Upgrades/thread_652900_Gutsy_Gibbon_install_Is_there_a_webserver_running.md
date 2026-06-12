---
title: "Gutsy Gibbon install: Is there a webserver running?"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by grantd on 2007-12-29
I'm new to Ubuntu (but not Linux), and wonder how CUPS admin is managing to serve webpages, since Apache isn't tunning. Is some other daemon providing webserver services? Some pointers would be welcome.

---

### Post by kidders on 2007-12-30
Hi there,

CUPS on Ubuntu runs just the same as it does on any other platform. It has its own internal web server. Since IPP is layered on top of HTTP, CUPS can't function without one ... Running something as unwieldy as Apache is unnecessary though.

---

