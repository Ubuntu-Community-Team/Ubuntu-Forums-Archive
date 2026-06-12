---
title: "Error"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Ranax on 2009-08-15
I can't install anything through Synaptic, Add/Remove or via Terminus as I get;

```

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```I've tried; ```
sudo dpkg --configure -a
``` But it doesn't work.

---

### Post by paul_in_london on 2009-08-15
Try this:

```
sudo rm -f /var/lib/apt/lists/*
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo aptitude update
sudo aptitude upgrade

```

---

### Post by Ranax on 2009-08-15
Doesn't work, I get this;

```
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
```

---

### Post by paul_in_london on 2009-08-15
That's fine. You don't need to remove that directory. Just ignore that message!

---

### Post by Ranax on 2009-08-15
It worked! Thanks! :)

---

