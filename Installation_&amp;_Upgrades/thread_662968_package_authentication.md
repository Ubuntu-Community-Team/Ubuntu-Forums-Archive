---
title: "package authentication"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by kiiz on 2008-01-09
i use kpackage but when downloading it say packages cant be authenticated . same with synaptic . please how do i resolve this

---

### Post by taurus on 2008-01-09
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

