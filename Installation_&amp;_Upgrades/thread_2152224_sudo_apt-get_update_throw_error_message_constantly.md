---
title: "sudo apt-get update throw error message constantly"
date: 2013-06-07
forum: Installation &amp; Upgrades
---

### Post by oren tal on 2013-06-07
Whenever I do sudo apt-get update, Iget the following message:
```
W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources  404  Not Found

W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources  404  Not Found

W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources  404  Not Found

W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources  404  Not Found

W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/natty-backports/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/natty-backports/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/binary-i386/Packages  404  Not Found

W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/binary-i386/Packages  404  Not Found

W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/binary-i386/Packages  404  Not Found
```

How can I fix this?

---

### Post by slickymaster on 2013-06-07
You're using a mirror that is down or not updated. See[ How can I get apt to use a mirror close to me?]("http://askubuntu.com/q/37753/6969") for a way to change mirrors.

---

### Post by fantab on 2013-06-07
'Natty' or Ubuntu 11.04 is dead. Meaning it has reached its '[end of life]("https://wiki.ubuntu.com/Releases")', and Ubuntu no longer supports it. So you will not get any updates to it. The repositories for 'natty' don't exist.

Install the latest version of Ubuntu or Ubuntu LTS.

---

