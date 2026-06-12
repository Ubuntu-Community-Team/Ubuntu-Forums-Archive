---
title: "there is a problem with the dependencies of gnome-user-share"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-18
it seem to be that it doesn't automaticly install apache2.2-bin and libapache2-mod-dnssd
so when you open gnome-user-share it said the feature cannot be enabled because the require pacages are not installed on your system.

i'm pretty sure that there is a bug report about it in launchpad but the problem still exist 

and by the way i tried installing it like this:

sudo apt-get apache2.2-bin libapache2-mod-dnssd and got this:

E: Invalid operation apache2.2-bin

am i doing something wrong?

thanks in advance.

---

### Post by linuxman94 on 2010-03-28
It should be:

```
sudo apt-get **install** apache2.2-bin libapache2-mod-dnssd 
```

---

### Post by aviramof on 2010-03-29
10x i forgot about it then.:)

---

