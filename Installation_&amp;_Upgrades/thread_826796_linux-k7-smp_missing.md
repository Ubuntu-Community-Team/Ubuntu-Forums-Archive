---
title: "linux-k7-smp missing?"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by lol_ubanto on 2008-06-12
Hi,

I just installed Ubuntu 8.04 and trying to upgrade the kernel with:

```
apt-get install linux-k7-smp
```

But it doesn't seem to exist in the repository. Anything I'm missing here? I've enabled all repositories in Synaptic and still can't find anything for a search on k7-smp...

Thanks in advance!

---

### Post by forger on 2008-06-12
linux-k7 386 686 etc. do not exist anymore, they have been "generalized" to one package: linux-generic

---

### Post by PmDematagoda on 2008-06-12
From what I remember the k7 variant of the kernel was dropped since there was not much of a performance improvement between the generic and the k7 kernel.

---

### Post by PmDematagoda on 2008-06-12
I am not sure if these are real k7 packages, but there seem to be some k7 packages [here]("http://packages.ubuntu.com/search?keywords=k7&searchon=names&suite=hardy&section=all").

---

### Post by forger on 2008-06-12
that's a dummy package
[http://packages.ubuntu.com/hardy/linux-image-k7](http://packages.ubuntu.com/hardy/linux-image-k7) links to linux-image-generic :)

---

