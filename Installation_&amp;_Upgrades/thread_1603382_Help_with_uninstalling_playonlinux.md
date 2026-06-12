---
title: "Help with uninstalling playonlinux"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by theyoyoist on 2010-10-22
I have had issues with uninstalling playonlinux, when I open synaptic package manager it tells my this.
E: Type '--2010-10-21' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report

When I tried the terminal sudo apt-get purge playonlinux 

E: Type '--2010-10-21' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.

---

### Post by Sef on 2010-10-22
How did you install Play on Linux?

---

### Post by theyoyoist on 2010-10-22
Through the Ubuntu Software Center

---

### Post by theyoyoist on 2010-10-22
And it will not let me do anything on terminal or synaptic i get the same message

---

### Post by sikander3786 on 2010-10-22
Try this.

```
cd /etc/apt/sources.list.d
```

```
sudo cp playonlinux.list playonlinux.list.old
```

```
sudo rm playonlinux.list
```

And then

```
sudo apt-get update
```

---

### Post by theyoyoist on 2010-10-22
Help please

---

### Post by theyoyoist on 2010-10-22
Thank you so much, problem solved like magic. :)

---

### Post by RockStarzInc on 2010-12-04
:popcorn:     I'm impressed. I was about to have to crash my whole system. I thought I was S.O.L.
Thank you sikander3786

---

