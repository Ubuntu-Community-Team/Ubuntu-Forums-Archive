---
title: "error: no acceptable C compiler found in $PATH"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by yuly4n on 2011-02-28
error: no acceptable C compiler found in $PATH
 
i have an ubuntu 10.10

---

### Post by SeijiSensei on 2011-02-28
sudo apt-get install build-essential

will download and install what you need to compile most things.  If you're trying to build your own copy of an application also available from the repositories, you also need to run

sudo apt-get build-dep [name of package]

which will download any needed dependencies like headers.

---

### Post by devilworld2 on 2013-02-15
thanks SeijiSensei

using your advice for lubuntu, as i'm a linux noob

---

