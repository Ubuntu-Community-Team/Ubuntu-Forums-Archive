---
title: "apt-get selecting wrong kernel?"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by lavinog on 2010-02-14
I used the command:
```

sudo apt-get remove linux-headers-2.6.31-1*

```
thinking it would remove the headers that are less than 2.6.31-20, but it selected 20 also:
```

Note, selecting linux-headers-2.6.31-20 for regex 'linux-headers-2.6.31-1*'

```
Why did it do this?

Using 2.6.31-1[6-8]* selected the ones I wanted to remove.  I am just curious why the first method almost removed everything?

---

