---
title: "[SOLVED] How can I unistall Moblock?"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by OsakaWilson on 2007-10-20
My upgrade is stalled because of some error related to Moblock. See below.

Failed to fetch [http://moblock-deb.sourceforge.net/debian/dists/feisty/Release](http://moblock-deb.sourceforge.net/debian/dists/feisty/Release) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

Can anyone tell my how to fix this? 

I would be perfectly happy to uninstall Moblock if that will allow the upgrade to continue. In which case, how do you uninstall Moblock? It is does not come up in Synaptic or Add/Remove.

---

### Post by ebastos on 2007-10-20
Hello, 

You can try:


```
sudo gedit /etc/apt/sources.list
```

Then comment (by inserting a "#" in the beginning of the line) the following entries:

```
deb http://moblock-deb.sourceforge.net/debian feisty main
deb-src http://moblock-deb.sourceforge.net/debian feisty main
```

It's going to look like that:

```

# deb http://moblock-deb.sourceforge.net/debian feisty main
# deb-src http://moblock-deb.sourceforge.net/debian feisty main
```

Save your file and then execute: 

```
sudo apt-get update
```

Now you are probably good to continue your update.

[]'s
Eri

---

### Post by OsakaWilson on 2007-10-20
It's working. Thank you very much!

---

