---
title: "Gksu ... -c -d (no distro upgrade message)"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by madman91 on 2007-04-28
Hello,
I am having a problem with my computer. When I use the "official upgrade method" (a.k.a gksu "update-manager -c -d" or any of the -c -d combinations) the dialog pops up and every runs great. I hit the check button, it scans through my sources.list (which is good, got it from ubuntuguide) and no "New distrobution" message pops up.

This is a 

32bit Dapper with all current upgrades / dist-upgrades,

Any ideas?

Thanks,
MaDman

---

### Post by madman91 on 2007-04-29
This is really bothering me. I am trying the apt-get way, and it is working. But I would prefer to use the "official" upgrade method.

---

### Post by joncheyne on 2007-04-30
Lots of people in the same boat ... some bugs already logged.

---

### Post by madman91 on 2007-04-30
So any idea as to why this is happening, how to fix it, and when it will be solved? (update:: the system is now using apt-get to upgrade to feisty)

---

### Post by zvacet on 2007-05-01
Do you still run Dapper?If you do you have to upgrade to Edgy.
```
gksu "update-manager -c" 
```

After that replace your source list
```
  sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
```

```
sudo aptitude update && sudo aptitude upgrade
```

Now you have up-to -date Edgy and you are ready to upgrade to Feisty

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

Replace source list when you are finish

```
 sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by madman91 on 2007-05-01
> **zvacet said:**
> Do you still run Dapper?If you do you have to upgrade to Edgy.
```
gksu "update-manager -c" 
```After that replace your source list
```
  sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
``````
sudo aptitude update && sudo aptitude upgrade
```Now you have up-to -date Edgy and you are ready to upgrade to Feisty

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Replace source list when you are finish

```
 sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
``````
sudo aptitude update && sudo aptitude upgrade
```

Hey, thanks for the information. Unfortunately I have already upgraded that computer with this method. It is now running 32bit Feisty. 

Thanks anyways!

---

