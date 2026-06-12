---
title: "installing packages via command line"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by adrianp918 on 2011-08-24
i am trying to install upgrades for my ubuntu server via webmin, 

and i put in the command apt-get install imagemagick 

and when i do  that i see the output and it asks me if i want to install, 

is there a command that will automatically force the installation so that way i dont have to hit yes or Y?

---

### Post by sikander3786 on 2011-08-24
You can simply add the '-y' switch.

```
sudo apt-get install <package> -y
```

---

### Post by adrianp918 on 2011-08-24
Thank you so very much

---

