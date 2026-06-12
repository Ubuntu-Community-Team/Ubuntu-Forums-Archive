---
title: "installing NVU [Resolved]"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by shazbot on 2006-11-21
Can anyone tell me how to install NVU, as its not in my synaptic and I can never install download packages as that is just to complicated (to many years just clicling en a xxx.exe program)

am running edgy, thanks

Have sussed it, did a aptitude install and it worked :)

---

### Post by aysiu on 2006-11-21
Step 1.
[Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

Step 2. ```
sudo aptitude update
sudo aptitude install nvu
```

---

### Post by adamkane on 2006-11-21
I don't use Edgy, but you probably need to enable the Universe Repository via source-o-matic:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by shazbot on 2006-11-21
Thanks, sussed it as you replied, many thanks

---

