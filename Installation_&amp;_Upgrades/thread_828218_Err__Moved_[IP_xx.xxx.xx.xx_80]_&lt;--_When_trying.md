---
title: "Err:  Moved [IP: xx.xxx.xx.xx 80] &lt;-- When trying to update 8.04 server"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by rushinblue on 2008-06-13
I am trying to update Ubuntu Server 8.04 using 

```
sudo aptitude update
```

I get the following messages:

```
Ign http://us.archive.ubuntu.com hardy-updates/main Sources

```
```

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
 302 Moved [IP: 91.1689.8846 80]
```

Any idea what this means?

Do I need to edit the /etc/apt/sources.list ?

Thanks

---

### Post by jimv on 2008-06-13
Could be temporary failure for that repo....I'd try again in a few hours.

---

### Post by rushinblue on 2008-06-13
Thanks, I will try that.

---

