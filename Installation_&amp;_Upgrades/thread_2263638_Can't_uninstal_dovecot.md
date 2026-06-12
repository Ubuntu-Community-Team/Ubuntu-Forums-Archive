---
title: "Can't uninstal dovecot"
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by asdasd4 on 2015-02-02
Try any thing none work ,won't deleting (**i logged in as root**):

```
 aptitude purge dovecot
```

```
apt-get remove dovecot
```

```
sudo apt-get remove --auto-remove dovecot
```

 ```
apt-get install -f dovecot
```

```
sudo apt-get remove --purge postfix
```

 ```
sudo apt-get purge --auto-remove dovecot-postfix
```

Nothing work's this error :
```
 
Reading package lists... Done
Building dependency tree
Reading state information... Done
[SIZE=4]**Package 'dovecot' is not installed, so not removed**[/SIZE]
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

```

When i try sudo service dovecot status i get this :
```
dovecot start/runing
```

Please please how i remove dovecot!!! i already removed postfix but i no success remove dovecot , i also can give SSH access just to solve it!!

Thanks .

---

### Post by ajgreeny on 2015-02-02
How did you install it in the first place?

---

### Post by asdasd4 on 2015-02-02
apt-get install dovecot ?

---

### Post by slickymaster on 2015-02-02
> **ajgreeny said:**
> How did you install it in the first place?
This ^^^
> **asdasd4 said:**
> <---snip--->
```
sudo apt-get remove --auto-remove dovecot
```
<---snip--->
```
sudo apt-get purge --auto-remove dovecot-postfix
```<---snip--->
Another thing, the correct syntax is **autoremove**, not auto-remove.

---

