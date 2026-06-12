---
title: "APT: How to remove all libraries belonging to a installed package?"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by Treppenhouse on 2013-02-16
Hello!

I recently installed a program using the Ubuntu Software Center (apt-get). However, this package had several dependencies (mostly libraries that had to be installed as well).

After some time, I realized this program does not suit my needs, so I want to remove it.

Question: Is there a way not only to remove the package/program itself, but also all libraries and everything that was installed priorly,  because of this program?

Thanks in advance for your help!

P.S. I am using Ubuntu. Newest Version (12.10)

---

### Post by JRV on 2013-02-16
Try this:
```

sudo apt-get purge [PACKAGE}
sudo apt-get autoremove

```

---

### Post by Treppenhouse on 2013-02-16
Thanks! Exactly what I was looking for!

---

