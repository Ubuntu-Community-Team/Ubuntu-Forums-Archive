---
title: "Identify the package a file belong to and running out or root space."
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by surferX on 2010-04-08
I just ran run of the routine upgrades, which has given me a new kernel, and modules... and of course is now filling up allmost all of 250MG root partitiion. :-)

I have /lib/modules/2.6.31-14-generic/ which I am sure I no longer need now that I have 
/lib/modules/2.6.31-20-generic/

how can I identify what package the files from /lib/modules/2.6.31-14-generic/ came from so I can remove the package and reclaim the space? rather than just delete it

---

### Post by diesch on 2010-04-08
```
dpkg -S /lib/modules/2.6.31-14-generic/
```

---

