---
title: "dpkg --configure -a"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by F150 on 2008-09-28
I have been trying to run the update manager for some time now and when i do it tells me i need to run dpkg --configure -a, then when I type that in my terminal it says I need to be a superuser to run. I have no Idea what this means and I really need some help so if you know what I should do please tell me....
Thanks

---

### Post by SuperSonic4 on 2008-09-28
Superuser means prefacing the command with sudo which gives root/superuser powers. Paste the following command into terminal and press enter

```
sudo dpkg --configure -a
```

---

