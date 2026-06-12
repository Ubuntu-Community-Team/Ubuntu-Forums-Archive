---
title: "i can`t get update or upgrade add or remove"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by sa3paleasm on 2009-12-18
i`ve a problem i get some package for some program or idon`t remeber cause i don`t the system long time ago i`ve mass. everytime about line 5 i don`t know where is that 

```
[sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
/CODE]

[code]sudo apt-get autoremove
E: Malformed line 5 in source list /etc/apt/sources.list (URI parse)
```
```
sudo apt-get update && sudo apt-get upgrade
E: Malformed line 5 in source list /etc/apt/sources.list (URI parse)
``````
apt-get update
     E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)

```i`m sorry i don`t know too much about Kubuntu 9.10 

:popcorn:

---

### Post by EricDrijv on 2009-12-18
Gedit is a gnome editor
use kate instead

---

### Post by sa3paleasm on 2009-12-19
thanks i never know i think i can use gnome order in kde

---

### Post by EricDrijv on 2009-12-19
> **sa3paleasm said:**
> thanks i never know i think i can use gnome order in kde

sudo kate /etc/apt/sources.list

---

### Post by snowpine on 2009-12-19
I would recommend 'kdesu kate' instead of 'sudo kate'.

If you need help figuring out the problem with line 5, you can cut & paste it here.

---

