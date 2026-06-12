---
title: "[SOLVED] g++"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by vikasmk on 2008-03-01
hi, I am having problems installing g++ on my pc 
 i tried sudo apt-get install heres what happened
```
vikasmk@vikasmk:~$ sudo apt-get install g++
[sudo] password for vikasmk:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++-4.1 libstdc++6-4.1-dev
Suggested packages:
  g++-multilib g++-4.1-multilib gcc-4.1-doc libstdc++6-4.1-doc
The following NEW packages will be installed:
  g++ g++-4.1 libstdc++6-4.1-dev
0 upgraded, 3 newly installed, 0 to remove and 44 not upgraded.
Need to get 0B/3730kB of archives.
After unpacking 13.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)'
in the drive '/cdrom/' and press enter


```

---

### Post by zvacet on 2008-03-01
Why don´t you put Cd in drive as you asked to?Second option is 

```
gksudo gedit /etc/apt/sources.list
```

and put # in front of Cd line like this

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

Save and close.

```
sudo apt-get update
```

Now you can install package you want.

---

### Post by vikasmk on 2008-03-02
thanx it worked....
 could you tell me exactly why it worked when i inserted the '#':)
  thanx again

---

### Post by Pumalite on 2008-03-02
Cannot be read as a source anymore.

---

