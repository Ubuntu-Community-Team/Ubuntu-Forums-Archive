---
title: "linux-image-2.6.22-14-generic will not install"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by osonegro on 2008-01-24
I got a notice that said that updates needed to be installed, they all installed correctly except for linux-image-2.6.22-14-generic.

I get this message everytime.

E: /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2

What can I do to solve this??

---

### Post by PmDematagoda on 2008-01-24
Remove that file using:-
```
sudo rm /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb
```

And then try doing the update again.

---

### Post by osonegro on 2008-01-24
Thanks that did the trick!

---

