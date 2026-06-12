---
title: "after Ubuntu Installation"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by mahendrahpu on 2010-07-27
hi

I installed ubuntu 8 form DVD. thereafter how we can play songs ,video and install 
software from DVD. I don't have internet connection.
 how this possible...........

---

### Post by zvacet on 2010-07-28
If any of your friends have internet download ubuntu-restricted-extras from [here]("http://packages.ubuntu.com/") ( choose your distribution) and dowload all packages marked with green.Put all packages in one folder and move it to your comp with USB/CD...Once you put that folder in Ubuntu (in your home folder) go inside that folder (let say that name of the folder is **upack**).In applications>accessories>terminal write

```
cd upack
```

hit enter

```
sudo dpkg -i *deb
```

hit enter again and your packages will be installed.

---

### Post by mahendrahpu on 2010-07-31
hi thanks for reply
my ubuntu pacage is ubuntu 8.10 intrepid ibex.  I open your suggested link
I saw these link;
[dapper]("http://packages.ubuntu.com/dapper/") (6.06LTS) 
[dapper-update]("http://packages.ubuntu.com/dapper-updates/")s 
[dapper-backports]("http://packages.ubuntu.com/dapper-backports/") 
[hardy]("http://packages.ubuntu.com/hardy/") (8.04LTS) 
[hardy-updates]("http://packages.ubuntu.com/hardy-updates/") 
[hardy-backports]("http://packages.ubuntu.com/hardy-backports/") 
[jaunty]("http://packages.ubuntu.com/jaunty/") (9.04) 
[jaunty-updates]("http://packages.ubuntu.com/jaunty-updates/") 
[jaunty-backports]("http://packages.ubuntu.com/jaunty-backports/") 
[karmic]("http://packages.ubuntu.com/karmic/") (9.10) 
[karmic-updates]("http://packages.ubuntu.com/karmic-updates/") 
[karmic-backports]("http://packages.ubuntu.com/karmic-backports/") 
[lucid]("http://packages.ubuntu.com/lucid/") (10.04LTS) 
[lucid-updates]("http://packages.ubuntu.com/lucid-updates/") 
[lucid-backports]("http://packages.ubuntu.com/lucid-backports/") 
[maverick]("http://packages.ubuntu.com/maverick/")  

could  you tell me which one i can choose
for download.I checked some of them but i thinke there is no packages marked with green.

---

### Post by zvacet on 2010-08-01
You are running unsupported Ubuntu version,so it will be good to install Lucid ( Ubuntu 10.4).If you decide to do that first back up all your valuable data.It will be good to make separate home partition to.If you have separate home partition your settings &files will be safe in case of reinstall,fresh install...

---

