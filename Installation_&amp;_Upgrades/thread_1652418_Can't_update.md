---
title: "Can't update"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by volatilepyro on 2010-12-24
I recently installed ubuntu on my mum's dell dimension 3000 and now it won't update anything. It says that it's a connection problem and to check the Internet connection but the Internet works fine. Any advice will be much appreciated.

---

### Post by Rubi1200 on 2010-12-25
Hi,
we need more information please.

1. what version of Ubuntu and how did you install it?

2. what other error messages, if any, did you see?

3. run these commands and post the output for us:

go to Applications > Accessories > Terminal

```
sudo lshw -C network
```

```
ifconfig
```

```
sudo dpkg --configure -a
```

Thanks.

---

