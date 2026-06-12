---
title: "debconf-get-selections doesnt work!"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by withjigs on 2011-04-24
Hello everyone,
Trying to create initial preseed file using debconf-get-selections, but getting following error.
```

root@jbox:~# debconf-get-selections --installer
debconf: DbDriver "di_questions": could not open /var/log/installer/cdebconf/questions.dat

```
I am using Ubuntu 10.10.

Thanks,
Jigar

---

### Post by hedge.hog on 2011-05-07
Drop the --installer option and it should work for you:

    root@jbox:~# debconf-get-selections 

HTH?

---

