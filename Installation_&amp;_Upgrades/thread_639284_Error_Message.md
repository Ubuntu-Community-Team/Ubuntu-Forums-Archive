---
title: "Error Message"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by sevenworth on 2007-12-13
Hi,

What does this error mean, and how do I repair it?

> E: Dynamic MMap ran out of room
E: Error occurred while processing koffice-doc-html (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-backports_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


---

### Post by PmDematagoda on 2007-12-13
Do:-
```

sudo apt-get update
```

And see if that might solve your problem.

---

### Post by bapoumba on 2007-12-13
Please try:
```
$ sudo apt-get update -o APT::Cache-Limit=25165824
```

---

