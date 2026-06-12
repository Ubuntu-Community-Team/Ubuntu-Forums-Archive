---
title: "Problem: Can't upgrade or install anything."
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by spiney_norm on 2008-06-04
Ok so I upgraded to 8.04 like everyone else, it went fine, but now I can't use the Package Manager, I can't use the "Add/Remove applications, and I can't install updates. Whenever I try to install or upgrade something the System Authentication window tries to come up, but it never loads and the Update manager or whatever I'm using just sits there as though its loading or expecting me to type in my password. I have had no other problems with authentication, just when i'm trying to upgrade or install apps. I have no idea what I'm doing wrong, any help would be appreciated.

---

### Post by Rocket2DMn on 2008-06-04
Can you please run
```
sudo apt-get update
sudo apt-get upgrade
```
If it gives unusual output, please post it back.

---

### Post by aysiu on 2008-06-04
Can you install anything from [the command line](http://www.psychocats.net/ubuntu/terminal)? ```
sudo apt-get update
sudo apt-get install *nameofpackage*
```

---

### Post by spiney_norm on 2008-06-04
Nothing out of the ordinary there. Although I am pretty new to this, but by the look of it, it seems to be installing all the recent updates.

---

### Post by Rocket2DMn on 2008-06-04
After the updates, does the problem still occur?

---

### Post by spiney_norm on 2008-06-05
Yea, Same thing happens

---

### Post by aysiu on 2008-06-05
Can you paste this command into the terminal and then paste the output back here? ```
gksudo update-manager
```

---

