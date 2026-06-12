---
title: "canon lbp3000 printer installation"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by wil433 on 2008-11-24
I am in the process of transferring from XP to Ubuntu (8.10). I wish to install drivers for a Canon LBP3000 printer. I have downloaded the driver tarball from [www.canon.com.au](www.canon.com.au) website and unpacked it.

Using the Gdebi installer uncovered some dependency requirement. One of these is libglib1.2 and the installed libglib1.2ldbl wont work. I tried a soft point: 
sudo ln -s ./libglib1.2ldbl ./libglib1.2
but to no effect.

Assistance required, please.

---

### Post by Partyboi2 on 2008-11-25
try installing libglib1.2-dev package.
```
sudo apt-get install libglib1.2-dev
```[B]
[/B]

---

### Post by wil433 on 2008-11-26
Thanks Partyboi2, but no go. Still get 'Dependency is not satisfiable: libglib1.2'

---

