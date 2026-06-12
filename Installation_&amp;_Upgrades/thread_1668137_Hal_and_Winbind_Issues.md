---
title: "Hal and Winbind Issues"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by dmelendez34 on 2011-01-15
I installed ubuntu 10.10 on a desktop (athlon xp cpu, 1gb RAM, 160gb HDD) and everything went well but when I went to install some apps from the software center I got the error message that the install did not go through because of hal and winbind on everything thing I installed.  

I got the same error when update manager ran its updates and they installed.  

I tried uninstalling hal and winbind and reinstalling them but when I did that I got an error.  They both installed but apparently not completely.  

I forgot to write down the error message but I am hoping someone has a solution that I was unable to find during the 3 searches I made on this forums.

---

### Post by dmelendez34 on 2011-01-15
I forgot to mention that the apps I installed, mostly games, all run fine even with the errors I got....

...can I just uninstall hal and winbind and not worry about needing them at all?

---

### Post by Rubi1200 on 2011-01-16
Are there errors returned from running the following commands?

```
sudo apt-get install -f

sudo dpkg --configure -a
```

---

