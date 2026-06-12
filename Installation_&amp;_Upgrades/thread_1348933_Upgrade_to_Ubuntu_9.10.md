---
title: "Upgrade to Ubuntu 9.10"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by MEMackintosh on 2009-12-07
[SIZE=3][FONT=Comic Sans MS]Hi,

I recently upgraded by downloading Ubuntu 9.10 from Ubuntu 9.04. When the computer starts up it says it is loading Ubuntu 9.10, but when the Ubuntu home page shows up, the URL reads Ubuntu 9.04. Why?:confused: Also I have a problem with the 'page' freezing in place and I cannot do anything for several minutes.:confused:

Margaret
[/FONT][/SIZE]

---

### Post by zvacet on 2009-12-07
```
lsb_release -a
```

will tell you witch version do you run.You may try 

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

