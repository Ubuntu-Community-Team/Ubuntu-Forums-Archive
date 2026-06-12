---
title: "This has to be easy for you guys"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by edlentz on 2006-10-02
I installed Apache 2  and I want the document root to be /var/www instead of /var/www/apache2-default.  I can't find where to change this.  Can some one give me a hand here?

Thanks

Ed

---

### Post by amohanty on 2006-10-03
In a terminal:

[B]sudo locate -u
locate apache2.conf[/B]

In that file look for DocumentRoot

If its not there:
**locate httpd.conf**

and do the same

HTH
AM

---

