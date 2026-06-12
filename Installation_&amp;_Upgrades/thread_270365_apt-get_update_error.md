---
title: "apt-get update error"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by robin.w on 2006-10-03
Hello,

today I've tried to update my distro but when I typed "apt-get update" and after I obtained the message below:

```
Hit http://fi.archive.ubuntu.com dapper-updates/restricted Sources
Get:4 http://fi.archive.ubuntu.com dapper/main Sources [336kB]
99% [4 Sources gzip 0]
gzip: stdin: not in gzip format
Err http://fi.archive.ubuntu.com dapper/main Sources
  Sub-process gzip returned an error code (1)
Fetched 4B in 0s (9B/s)
```

Does anybody know how to fix that???

---

### Post by Kateikyoushi on 2006-10-03
Try it with another repo or retry later ?
Seems it should be 396K and only gets 9bytes.

---

