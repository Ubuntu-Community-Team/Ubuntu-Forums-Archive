---
title: "/dev/null partition"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by meithan on 2011-07-09
I was wondering: how big should my /dev/null partition be? I usually set it to 10GB but I'm not sure this is enough.

---

### Post by matt_symes on 2011-07-09
Hi

> **meithan said:**
> I was wondering: how big should my /dev/null partition be? I usually set it to 10GB but I'm not sure this is enough.

/dev/null is not a  disc partition.

```
matthew@matthew-laptop:~$ ls -l /dev/null
crw-rw-rw- 1 root root 1, 3 2011-07-09 12:30 /dev/null
matthew@matthew-laptop:~$ 
```[http://en.wikipedia.org/wiki//dev/null](http://en.wikipedia.org/wiki//dev/null)

Kind regards

---

