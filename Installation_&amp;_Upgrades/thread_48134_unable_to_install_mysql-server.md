---
title: "unable to install mysql-server"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by shawn.b on 2005-07-11
$ apt-get install mysql-server

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

using a remote ssh connection
any help would be apprieciated.

thanks

---

### Post by kvidell on 2005-07-11
[QUOTE=shawn.b]$ apt-get install mysql-server

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

using a remote ssh connection
any help would be apprieciated.

thanks[/QUOTE]
 Is anyone else using aptitude/apt-get/synaptic?
Only one instance of any of those can be open at a time.```
lsof | grep /var/lib/dpkg
```should tell you if anyone is using it.
You can also do a ps aux and visually scan for any of those items.
- Kev

---

### Post by shawn.b on 2005-07-11
# lsof | grep /var/lib/dpkg

gam_serve  7090      shawn   56r      DIR        3,1     4096    4398690 /var/lib/dpkg
synaptic  15697       root    7uW     REG        3,1        0    4398712 /var/lib/dpkg/lock
synaptic  15697       root    8r      REG        3,1   804143    4399968 /var/lib/dpkg/status
synaptic  15697       root   18r      REG        3,1   804849    4399996 /var/lib/dpkg/status
synaptic  15697       root   41r      REG        3,1   807761    4400043 /var/lib/dpkg/status
synaptic  15697       root   61r      REG        3,1   809841    4399338 /var/lib/dpkg/status


how do i fix this 

thanks

---

### Post by IchBin on 2005-07-11
[QUOTE=shawn.b]# lsof | grep /var/lib/dpkg

gam_serve  7090      shawn   56r      DIR        3,1     4096    4398690 /var/lib/dpkg
synaptic  15697       root    7uW     REG        3,1        0    4398712 /var/lib/dpkg/lock
synaptic  15697       root    8r      REG        3,1   804143    4399968 /var/lib/dpkg/status
synaptic  15697       root   18r      REG        3,1   804849    4399996 /var/lib/dpkg/status
synaptic  15697       root   41r      REG        3,1   807761    4400043 /var/lib/dpkg/status
synaptic  15697       root   61r      REG        3,1   809841    4399338 /var/lib/dpkg/status


how do i fix this 

thanks[/QUOTE]
 kill the process 15697

---

