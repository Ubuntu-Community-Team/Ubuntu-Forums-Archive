---
title: "spamassassin is missing"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by Belette on 2006-03-13
Hello !

I tried to install spamassassin with 
apt-get install spamassasin, but the system cannot find the package.
moreover, apt-cache seach spamassassin cannot find anything

is there repositories i can add ?
Thx a lot


Belette

---

### Post by Koybe on 2006-03-13
It's in the universe repo. You can add it via [synaptic](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages) or by editing your /etc/apt/source.list

---

### Post by Belette on 2006-03-14
Hi !

The problem is...

```
http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg: Connexion à archive.ubuntu.com: 80 (82.211.81.182) impossible. - connect (111 Connexion refusée)
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: Connexion à archive.ubuntu.com: 80 (82.211.81.182) impossible. - connect (111 Connexion refusée)
```

and i do not know why since internet works properly..:-k :???:

---

