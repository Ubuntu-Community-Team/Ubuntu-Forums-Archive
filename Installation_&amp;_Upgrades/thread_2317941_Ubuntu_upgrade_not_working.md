---
title: "Ubuntu upgrade not working"
date: 2016-03-21
forum: Installation &amp; Upgrades
---

### Post by redmike on 2016-03-21
Hi, my ubuntu upgrade system isn't working (without me having done an upgrade) Anyone know how to fix it please?
error message error opening cache, no package header:
 ```
E:problem with MergeList/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en
```

Thanks, Mike

---

### Post by fantab on 2016-03-22
Post the output of the following:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by redmike on 2016-03-22
Thank you, that seems to have worked. Certainly the no entry sign has gone. Will know more in morning. Mike

---

