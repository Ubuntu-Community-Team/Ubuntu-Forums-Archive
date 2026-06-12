---
title: "Permission denied while trying to open /dev/sda1"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by hihihi100 on 2010-03-25
Hello:
 
When, from the live cd I try to execute
```
e2fsck -y /dev/sda1
```
 
All i get is:
 
```
Permission denied while trying to open /dev/sda1
you must have r/w access to the filesystem or be root
```
 
To be root, as I have read, I must type, in a terminal:
 
```
sudo nautilus
```
 
or
 
```
gksa nautilus
```
 
both open a new window, but I still dont know how to open a terminal being "root user"
 
Help please

---

### Post by n0dix on 2010-03-25
Open a simple terminal, gnome-terminal or xterm, and use ```
$ sudo
```, or you can do ```
$ su -
```

---

### Post by coffeecat on 2010-03-25
> **hihihi100 said:**
> Hello:
 
When, from the live cd I try to execute
```
e2fsck -y /dev/sda1
```


You need:

```
sudo e2fsck -y /dev/sda1
```

See:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by pastalavista on 2010-03-25
All you need to perform tasks as root is 'sudo'(or gksu for graphical programs) before the command ```
sudo e2fsck -y /dev/sda1
```

---

