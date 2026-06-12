---
title: "After an upgrade (16.04.3 to 18.04), my system shows as &quot;Xenial Xerus&quot;"
date: 2018-05-11
forum: Installation &amp; Upgrades
---

### Post by Benjamin_E._Calist on 2018-05-11
Some weeks ago, I upgraded my Ubuntu 16.04.3 to the new version 18.04, but I see my system version as Xenial (not always). For example:

If I write "lsb_release -a", it shows my system as "16.04 Xenial Xerus", but when I make an apt-get update or upgrade, I see my system (sometimes not) as Bionic Beaver. So, my question is: How can I solve this situation? By the way, the security upgrades are Xenial also.

Thanks in advance.

---

### Post by deadflowr on 2018-05-11
show
```
cat /etc/apt/sources.list
```

---

