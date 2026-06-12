---
title: "Kubuntu CD Repository Doesn't Work in 10.04"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by ahayes on 2010-05-02
I was trying to install packages from the Kubuntu CD to get the Broadcom driver installed but when it tried to load any of the packages on the CD it said they couldn't be found.  I ultimately ended up copying the packages from the CD and installing the packages and their dependencies by hand through the console.

---

### Post by zvacet on 2010-05-02
I ´m not using Kubunut so I hope this is right command (and I believe you knew it already)

```
kdesudo /etc/apt/sources.list
```

and see if # sign is in front of line refering to CD.If it is remove it.Save and close file.

```
sudo apt-get update
```

---

### Post by ahayes on 2010-05-02
That enables the repository, I had already done that.  Apt knows about the files, but can't find them, it's as if the disk was unmounted (the disk is mounted).

---

