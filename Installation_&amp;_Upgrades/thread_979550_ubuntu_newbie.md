---
title: "ubuntu newbie"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by abdu on 2008-11-12
i just installed ubuntu 8.10 as a program in my windows xp OS and i love itbut i am having several problems. i get notification that i have 61 updates available but i am not able to install them. a screen comes up and then there is a bar and then nothing happens. 2nd the synaptic packet manager doesnt work. 3rd icant install anything from the add/remove applications. i dont have any sound comic out of my Toshiba portege m400 laptop. i have tried to look for a solution using google but couldnt get any help. please help me with the steps to solve these problems. thanks.

---

### Post by Partyboi2 on 2008-11-12
Welcome to ubuntu! Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
sudo apt-get update
sudo apt-get upgrade 
```

---

### Post by abdu on 2008-11-14
this is what i get when i entered the code

sudo: must be setuid root

---

### Post by Partyboi2 on 2008-11-15
Can you also post the output of
```
 ls -l usr/bin/sudo 
```
to see if it has the correct permissions.

---

