---
title: "where to find a package name to install with apt-get ?"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by glabouni on 2007-01-14
Answering the question "how do you find a command that does what you want to do" in  "[Just a general question about installing/uninstalling]("http://ubuntuforums.org/showthread.php?t=331069")" thread reminded me that I was wondering where to find informations about a specific package or find a package name to install it through apt-get.

While I was trying to get [ftpcube]("http://ftpcube.sourceforge.net/") installed, in a search for a GUI ftp client that woud fit my needs, I ended up looking for a way to install a recent version of the required [wxpython]("http://www.wxpython.org/") and [paramiko](http://www.lag.net/paramiko/) SSH which in turn lead me to discover that [launchpad features a searchable database of ubuntu packages](https://launchpad.net/ubuntu/). 

So I decided to post here about it, this could be useful for someone who doesn't know about this. here are the links:

- edgy speficic packages: [https://launchpad.net/ubuntu/edgy/](https://launchpad.net/ubuntu/edgy/)
- dapper speficic packages: [https://launchpad.net/ubuntu/dapper/](https://launchpad.net/ubuntu/dapper/)
- hoary speficic packages: [https://launchpad.net/ubuntu/hoary/](https://launchpad.net/ubuntu/hoary/)

---

### Post by logos34 on 2007-01-14
> launchpad features a searchable database of ubuntu packages. 

So does Ubuntu
[http://packages.ubuntulinux.org/]("http://packages.ubuntulinux.org/")

---

### Post by kerry_s on 2007-01-14
Theres also a package search in the firefox search engines. Just click on the G for the drop down menu.

---

### Post by icefaerie on 2007-01-14
You can also do this:
```
sudo aptitude search whatever
```
Where whatever is whatever you're looking for. :D

---

### Post by aysiu on 2007-01-14
Or ```
apt-cache search *packagename*
```

---

### Post by glabouni on 2007-01-15
if you go for the command line, don't forget to update beforehands
```
sudo apt-get update
```
or
```
sudo aptitude update
```

not sure it allows you to search in disabled repositories though.
for example if you're looking for a universe package it may not show it universe repositories are disabled in apt-sources.

---

### Post by smartbei on 2007-01-15
Though it is slower, you can also use synaptic (System => Administration => Synaptic Package Manager)  to search...Somewhat more newbie friendly.

---

