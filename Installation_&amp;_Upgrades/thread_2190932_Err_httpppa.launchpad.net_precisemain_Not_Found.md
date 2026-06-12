---
title: "Err http://ppa.launchpad.net precise/main Not Found"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by snowweb on 2013-11-30
When I do `sudo apt-get update` I'm getting the following error:
```
Err http://ppa.launchpad.net precise/main Sources                                 
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found

```

Actually, early it said:
```
Err https://launchpad.net precise/main Sources                                 
  404  Not Found
Err https://launchpad.net precise/main i386 Packages
  404  Not Found

```

but I edited my sources file directly, hoping to solve it, but it is still not working.

---

### Post by snowweb on 2013-11-30
Ok. I've solved this by copying the sources from another machine. Thanks.

---

