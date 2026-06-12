---
title: "how to upgrade to jaunty from intrepid?"
date: 2009-03-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-03-21
```
scott2@scott2-desktop:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scott2@scott2-desktop:~$ 

```

this did not work?

ok, this did work 

sudo update-manager -d

---

### Post by anders_c_ on 2009-03-21
"update-manager -d"

the d stands for development releases

---

### Post by sdowney717 on 2009-03-21
how about
sudo apt-get dist-upgrade -d?

---

### Post by Bert Mariën on 2009-03-21
To upgrade, I should wait at least till after de RC.

---

### Post by taavikko on 2009-03-21
> **sdowney717 said:**
> how about
sudo apt-get dist-upgrade -d?

Negative, doesn't work.

Upgrade procedure is well documented in ubuntu's wikis.

---

