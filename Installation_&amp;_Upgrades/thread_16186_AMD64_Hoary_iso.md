---
title: "AMD64 Hoary iso"
date: 2005-02-19
forum: Installation &amp; Upgrades
---

### Post by Ronbo on 2005-02-19
Where can I downoad the latest AMD64 Hoary iso for an install?  Does anyone know the link?

---

### Post by dewey on 2005-02-19
You download the x86_64 Warty Iso, then upgrade to Hoary by using.
```
$sudo gedit /etc/apt/sources.list
```
And replacing all instances of 'Warty' with 'Hoary' and save.
Then:
```
$sudo apt-get update
$sudo apt-get dist-upgrade -y
```
And you should be good to go.

---

