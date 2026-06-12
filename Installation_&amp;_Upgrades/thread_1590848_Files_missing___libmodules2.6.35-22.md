---
title: "Files missing   /lib/modules/2.6.35-22"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by skyjacker on 2010-10-08
How can I correct this? I get this message during start up after I installed UNR 10-10.

---

### Post by andrewthomas on 2010-10-09
try to reinstall the image.

```
sudo aptitude reinstall linux-image
```

---

### Post by skyjacker on 2010-10-09
> **andrewthomas said:**
> try to reinstall the image.

```
sudo aptitude reinstall linux-image
```  

Your command didn't work, so I tried sudo apt-get install linux-image. this worked and it set up the missing files. However, this still didn't solve the problem.

Thanks for the help... Maybe a new suggestion??

---

### Post by andrewthomas on 2010-10-09
what is the exact message in your logs?

---

