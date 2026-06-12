---
title: "change programs installation path"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by gggggggg on 2013-04-16
Hi, i'm new in ubuntu. i want to install ntop but it has problem with RRDTOOl that want it was install to a particular path.how can i change RRDTOOL install path?

i use this commands:
./configure
make
make install

---

### Post by MG&amp;TL on 2013-04-16
Why do you want to install via source builds? You can install *ntop* right away:

```
sudo apt-get install ntop
```

In the (unlikely) event that you *do* need to build from source, normally with *configure* scripts, you use:

```
./configure --prefix=/some/path/to/install/path
```

to specify the installation path.

---

### Post by gggggggg on 2013-04-17
thanks for your reply.
if i use 
[COLOR=#000000]
sudo apt-get install ntop

[/COLOR]
it install old version of ntop.

---

### Post by MG&amp;TL on 2013-04-17
> **gggggggg said:**
> 
it install old version of ntop.

Is it that important? Anyway, you've got two choices:

1) Wait until 13.04 comes out shortly, presumably with an updated ntop.

2) Try the configure command I gave above.

---

