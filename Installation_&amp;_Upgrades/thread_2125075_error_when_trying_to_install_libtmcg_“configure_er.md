---
title: "error when trying to install libtmcg “configure: error: libgmp &gt;= 4.1 is needed”"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by tgsharp2100 on 2013-03-12
I've tried installing different libgmp's from ubuntu app center and I tried installing it manually from [http://gmplib.org/#DOWNLOAD](http://gmplib.org/#DOWNLOAD)  but I can't get this to configure it's an old library and I'm trying to  run it on the latest version of ubuntu but I didn't think I'd have  problems but I'm new to trying to use libraries like this any help would  be greatly appreciated.

---

### Post by schragge on 2013-03-13
What Ubuntu release are you running? Precise (Ubuntu 12.04LTS) has libgmp 5.0.5 which is more than enough to satisfy *libgmp >= 4.1 is needed*. Try ```
sudo apt-get install libgmp-dev
```

---

### Post by tgsharp2100 on 2013-03-13
Thanks for the response I'm using 12.10 the latest version nd*'ve already installed *libgmp-dev and I still get same message.

---

