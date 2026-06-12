---
title: "ut2004 won't uninstall"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by FunkyMunky on 2006-10-31
hi. yesterday i installed edgy on a fresh reformat and everything work flawlessly. then i tried to install ut2004 and i screwed something up and now i want to reinstall it but uninstall.sh in ut2004 game directory doesnt seem to work and it won't let me delete it manually saying that i don't have the right priviledges to do it. i believe it's possible to do it using sudo command in terminal but i dont know what should i type after "sudo" :confused: also note that i'm pretty new to ubuntu and don't know the terminal commands yet.

so please, help.

---

### Post by Hemmer on 2006-11-14
you can run nautilus as root which means you will have permissions to remove the installed files manually, using a graphical interface, which is much easier than using the terminal. do this by: 

```
sudo nautilus
```

---

