---
title: "Problem updating Hardy"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by OldPoppa on 2008-06-16
Please review [this description]("http://ubuntudiary.wordpress.com/37/") of the problem and what I've tried so far and then provide me with some direction, if you'd be so kind.

---

### Post by Partyboi2 on 2008-06-16
try```
 sudo apt-get update
```then
```
sudo apt-get upgrade
```

---

### Post by OldPoppa on 2008-06-16
> **Partyboi2 said:**
> try```
 sudo apt-get update
```...

fetched 807kB, read package lists, then warnings "duplicate sources.list entry" x 3

should i look for dupes in /etc/apt/sources.list and edit them out and then repeat "sudo apt-get update" b4 continuing?

---

### Post by Partyboi2 on 2008-06-16
yes, if unsure post your sources.list
```
cat /etc/apt/sources.list
```

---

