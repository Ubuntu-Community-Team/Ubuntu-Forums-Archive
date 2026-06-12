---
title: "bad sources.list?"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by afrazin on 2010-11-25
i just completed an upgrade from 7.04 to 10.04-LTS and now i'm trying to upgrade packages and it seems that the sources.list i'm using has errors saying temporary failure resolving the address.  Here's what my sources.list is:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse

any suggestions for better addresses?

thanks!

---

### Post by sikander3786 on 2010-11-25
Please post the complete output of this one as well.

```
sudo apt-get update
```

---

### Post by afrazin on 2010-11-25
thank you for your help.  i think i see the problem.  after applying a quick patch that had to do with our server's communication with the world, i was able to successfully get the updates.

---

