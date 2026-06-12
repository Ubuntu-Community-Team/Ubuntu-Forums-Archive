---
title: "How to save a software package in Ubuntu"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by supravat on 2009-12-09
In ubuntu to install a software package through terminal we use following command:

sudo apt-get install <package_name>

but I want to save the package, so that I can reinstall it later.

please help me...

---

### Post by MaindotC on 2009-12-09
From the apt-get man page:
```

-d, --download-only
           Download only; package files are only retrieved, not unpacked or
           installed. Configuration Item: APT::Get::Download-Only.

```

---

### Post by mikewhatever on 2009-12-09
The packages are downloaded into /var/cache/apt/archives. Just copy the package you want to save from there to a storage place.

---

### Post by rahilm on 2009-12-09
Observe what apt-get is downloading, then go to /var/cache/apt/archives 
find those files and copy them somewhere. If you later wish to install them again, you could.
1)Use Add downloaded packages in File menu in synaptic.
2)Install them one by one.
3)Copy them again into  /var/cache/apt/archives  and then run apt-get. It will not download at that time.

---

### Post by mick222 on 2011-11-18
You could also use apt ton cd  which will create a backup of all debs then you can use it like a repository or even install a custom Ubuntu from it.
Wrong thread sry

---

### Post by oldos2er on 2011-11-18
Closed, necromancy.

---

