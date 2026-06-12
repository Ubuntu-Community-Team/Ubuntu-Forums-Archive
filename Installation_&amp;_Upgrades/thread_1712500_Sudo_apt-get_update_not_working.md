---
title: "Sudo apt-get update not working?"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by aflyingturtle on 2011-03-22
For some reason my sudo apt-get update is returning a lot of 404's

```
 Fetched 316B in 5s (53B/s)
W: Failed to fetch [http://ppa.launchpad.net/tvst-hotmail/cardapio/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/tvst-hotmail/cardapio/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tvst-hotmail/cardapio/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/tvst-hotmail/cardapio/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any idea what's going wrong? I recently have been trying to install cardapio, and I think that maybe the cardopio servers have changed... But I want to get rid of these messages. Any ideas?

---

### Post by wilee-nilee on 2011-03-22
It is in a PPA.
[https://launchpad.net/cardapio](https://launchpad.net/cardapio)

You can change the servers in software sources, if you are failing altogether. The links you posted 404 as well on a direct click.

---

### Post by aflyingturtle on 2011-03-22
> **wilee-nilee said:**
> It is in a PPA.
[https://launchpad.net/cardapio](https://launchpad.net/cardapio)

You can change the servers in software sources, if you are failing altogether. The links you posted 404 as well on a direct click.

Thanks for the help.

---

