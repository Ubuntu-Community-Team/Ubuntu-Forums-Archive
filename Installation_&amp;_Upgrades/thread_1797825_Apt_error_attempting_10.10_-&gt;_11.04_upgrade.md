---
title: "Apt error attempting 10.10 -&gt; 11.04 upgrade"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by Enigmatic on 2011-07-05
I'm getting the following error which seems quite odd. Trying to change the server to my local country's update server results in the same error (with slightly different URL). I've also disabled any extra repositories I was using.

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/Release  Unable to find expected entry  extras/source/Sources in Meta-index file (malformed Release file?
```

When trying to upgrade to Natty I get the same error, just for the natty path:

```
W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/Release  Unable to find expected entry  extras/source/Sources in Meta-index file (malformed Release file?)
```

---

### Post by Enigmatic on 2011-07-05
I managed to fix this by deleting all but the most basic deb line. I'm not sure why this was happening because I wasn't referencing the extras repository, but it seems to have fixed it. Commenting everything out wasn't enough.

---

