---
title: "Broken packages - cannot upgrade"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by redshoes702 on 2010-05-15
The upgrade manager says: E:Unable to correct problems, you have held broken packages. And then it goes back to 9.10. How do I solve this?

---

### Post by kansasnoob on 2010-05-15
Try running the following commands in terminal and post the full terminal output:

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

---

### Post by redshoes702 on 2010-05-15
> **kansasnoob said:**
> Try running the following commands in terminal and post the full terminal output:

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

Thanks for your reply. Nothing happens.

---

