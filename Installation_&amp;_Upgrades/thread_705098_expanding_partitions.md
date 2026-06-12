---
title: "expanding partitions"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by Wake Rider on 2008-02-23
I have a 500 GB disk and am trying to resize the partitions Ubuntu & Windows using parted magic. It won't let me expand them, only downsize them. Help!:confused:

---

### Post by mikewhatever on 2008-02-23
Do you have any unallocated space to expand to? You can't expect to enlarge a partition over another one, can you.

---

### Post by radiocognition on 2008-02-23
Be sure to use G-Parted. It will allow you to resize your partitions.

```

sudo apt-get install gparted

```

---

### Post by Wake Rider on 2008-02-23
> **mikewhatever said:**
> Do you have any unallocated space to expand to? You can't expect to enlarge a partition over another one, can you.

This was the exact reason it wouldn't work. Thanks for your advice! :)

---

