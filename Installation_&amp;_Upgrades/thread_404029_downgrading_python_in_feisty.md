---
title: "downgrading python in feisty?"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by brucedes on 2007-04-07
I want to use cedega on feisty, but to do this, I need to downgrade my python to 2.4.4 (cedega doesn't seem to play nice with 2.5.1c1)

I did apt-get install pytho2.4, and it installed 2.4, but python -V still shows 2.5.1c1

How do I properly use python 2.4.4?

Thanks

---

### Post by zvacet on 2007-04-09
```
sudo dpkg -i /var/cache/apt/archives/python2.4.4
```

I don´t know if I typed correct name of your version,and if I didn´t you type correct one.

---

