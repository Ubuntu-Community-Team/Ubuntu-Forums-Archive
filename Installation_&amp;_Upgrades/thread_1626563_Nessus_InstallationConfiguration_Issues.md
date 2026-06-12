---
title: "Nessus Installation/Configuration Issues"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by Infinitum7 on 2010-11-20
Hey Forums,
     
  I wasn't totally sure if this was the correct forum, so i apologize if it is in the wrong forum. But anyway, after some tweaking i managed to get nessus installed on my machine. However i'm running into an issue when trying to add a user. 

The nessus daemon is running on my machine, i've registered. I think everything is peachy in that regard, but when i run:

```
zachadmin@ubuntu:~$ sudo /etc/init.d/nessusd restart
$Shutting down Nessus : .
$Starting Nessus : .
zachadmin@ubuntu:~$ sudo nessus-adduser
sudo: nessus-adduser: command not found

```Obviously the command not found is my error, from what i understand there isn't a default user placed in the first time. So essentially i have thie program installed, but i can't access it. Any help would be most appreciated. 

Thanks

---

### Post by morphy richards on 2010-11-26
i'm getting the same - i'm htinking i'm not in the correct nessus folder...

---

