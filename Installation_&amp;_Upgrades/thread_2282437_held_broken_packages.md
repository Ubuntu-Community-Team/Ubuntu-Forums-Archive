---
title: "held broken packages"
date: 2015-06-14
forum: Installation &amp; Upgrades
---

### Post by rakesh19 on 2015-06-14
Hello everybody..I am using ubuntu 14.04 LTS. When I trying to install g++ compiler I am getting   message in terminal as "xubuntu-live-settings : Depends: casper but it is not installableE: Unable to correct problems, you have held broken packages."

I tried the commands the following commands on terminal
                               sudo apt-get clean
                              sudo apt-get autoclean
                              sudo  apt-get update 
 but still I am getting the same error mesage..Could anyone help regarding this?
  Thanks in advance.

---

### Post by leclerc65 on 2015-06-14
In *synaptic* use option: edit/Fix broken packages

---

### Post by bapoumba on 2015-06-14
Should already been installed, which version are you looking for ?
[http://packages.ubuntu.com/trusty/g++-4.8](http://packages.ubuntu.com/trusty/g++-4.8)

Please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
sudo apt-get update
sudo apt-get upgrade
apt-cache policy gcc-4.8
```

---

