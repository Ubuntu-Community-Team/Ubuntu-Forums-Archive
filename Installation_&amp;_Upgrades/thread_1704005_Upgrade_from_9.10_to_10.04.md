---
title: "Upgrade from 9.10 to 10.04"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by greatcyrus on 2011-03-10
Dear all,
 
I had ubuntu 8.10 and i could upgrade it to 9.10 , but now i wanna to upgrade it to 10.04,but update manager tells me your system is up-to-date
 
what can i do?

---

### Post by Dutch70 on 2011-03-10
Welcome to UF greatcyrus

Open update manager, click settings on the bottom left. That will open software sources. Select the updates tab, and make sure it says "LTS releases only" under "release upgrades".

---

### Post by nomko on 2011-03-10
> **Dutch70 said:**
> Welcome to UF greatcyrus
 
Open update manager, click settings on the bottom left. That will open software sources. Select the updates tab, and make sure it says "LTS releases only" under "release upgrades".
 
It is better to perform a new fresh install. Like this, you avoid any problems in the future with configuration and/or setting files due to version conflicts.

---

### Post by Dutch70 on 2011-03-10
> **nomko said:**
> it is better to perform a new fresh install. Like this, you avoid any problems in the future with configuration and/or setting files due to version conflicts.

+1

---

### Post by garvinrick4 on 2011-03-10
#Another way by terminal:
```
sudo apt-get install aptitude
```
```
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 
```

---

### Post by mörgæs on 2011-03-10
It will be the third upgrade for the system. If anything goes wrong, you could try this:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

