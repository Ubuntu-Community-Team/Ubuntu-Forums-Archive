---
title: "Iso repository?"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by bindigi01 on 2008-02-15
Hi all
how to make a repository from the dvd ISO image??
some friends of me don't have net connection :)

---

### Post by zvacet on 2008-02-16
[Here.](ftp://tuma.ui.edu/pub/ubuntu-repository/gutsy/)

---

### Post by bindigi01 on 2008-02-16
i dont mean that i want to treat the installation dvd as repository:)

---

### Post by Partyboi2 on 2008-02-16
maybe [this]("http://ubuntuforums.org/showthread.php?t=352460")?

---

### Post by zvacet on 2008-02-16
```
gsudo gedit /etc/apt/sources.list
```

Remove # from line wich refer to CD/DVD.Save and close file.

```
sudo apt-get update
```

After thia every time you want to install something wich us on DVD you will see window with messa**ge insert DVD** or something similar.

---

### Post by zvacet on 2008-02-17
Are you looking for [this](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/32325) or [this](http://ubuntuforums.org/showthread.php?t=381972)?

---

