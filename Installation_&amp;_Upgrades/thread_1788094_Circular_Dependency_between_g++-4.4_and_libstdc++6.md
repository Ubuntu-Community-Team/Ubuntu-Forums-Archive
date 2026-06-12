---
title: "Circular Dependency between g++-4.4 and libstdc++6-4.4-dev"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by reza.b on 2011-06-22
[SIZE=2]Hi every body
I want to install RTAI in UBUNTU Lucid 10.04 in my PC which has not direct Internet connection. I download all packages for installing build-essential with another PC. I have installed all of them.
But when I want to install [/SIZE][SIZE=2][COLOR=Red]g++-4.4[/COLOR][/SIZE][SIZE=2], it depends to [/SIZE][SIZE=2][COLOR=Red]libstdc++6-4.4-dev[/COLOR][/SIZE][SIZE=2] and vice versa.

What can I do? please help :(
[/SIZE]

---

### Post by zvacet on 2011-06-22
```
sudo apt-get install g++-4.4 libstdc++6-4.4-dev
```

---

