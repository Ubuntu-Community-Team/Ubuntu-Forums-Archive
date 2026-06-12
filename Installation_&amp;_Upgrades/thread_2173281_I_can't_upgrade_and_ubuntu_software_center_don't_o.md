---
title: "I can't upgrade and ubuntu software center don't open."
date: 2013-09-08
forum: Installation &amp; Upgrades
---

### Post by dianavelo13 on 2013-09-08
I have this message when I try to upgrade 
 'E: encountered a section with no package: header, E: problem with mergelist/var/lib/apt/list/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_packages, E: the package list or status file could not be parsed or opened.' 
And when I try do upgrade with terminal I get the same error :( help please!!

---

### Post by Bashing-om on 2013-09-08
dianavelo13;
Let's say the index files are "bad" as per:
> 
the package list or status file could not be parsed or opened.' 

Remove the index files, will be restored in the latter command; Terminal codes:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```

Edit ! .. My welcome to the forum .. enjoy and learn much !

[INDENT][INDENT]should do ya good
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-09-08
Welcome to the forums. 

Just a note: ALWAYS run:

```
sudo apt-get up**date**
```

BEFORE you run:

```
sudo apt-get up**grade**
```

This is reflected in the last part of bashing-om's instructions. Cheers.

---

