---
title: "Delete /var/cache/apt/archives ?"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by IgnorantGuru on 2007-02-13
n/m - found the answer here http://ubuntuforums.org/showthread.php?t=100887

(can't figure out how to delete this post)

---

### Post by JamieC on 2007-02-13
Yes, it is. You can use the following command to remove them:
```

sudo apt-get clean

```

The cached packages most probably allow for faster re-installation (as they do not have to be downloaded again). It is also possible to use the downloaded package installers to create your  own repository (like APTonCD does).

---

### Post by Ptero-4 on 2007-02-13
It`s perfectly safe. Those files are the deb packages that get downloaded when you install apps through synaptic/aptitude. The apps themselves get installed in /usr, the debs are just the archives the apps come in, apt extract the data from those archives and installs it.

---

