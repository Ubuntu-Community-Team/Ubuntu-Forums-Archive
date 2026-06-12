---
title: "Problems installing Nessus"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by ramcosca on 2006-06-09
I stumbles across [this page]("http://easylinux.info/wiki/Ubuntu_dapper") and Nessus, the vulnerabilty scanner, called my attention. I tried installing it with the code that appears on the page, but it just aborts.

First part of the code:
```
sudo apt-get install nessus
sudo apt-get install nessusd
sudo nessus-adduser
sudo ln -fs /etc/init.d/nessusd /etc/rc2.d/S20nessusd
sudo /etc/init.d/nessusd start
sudo gedit /usr/share/applications/Nessus.desktop
```

Here's what appears on the terminal when I paste that in...
```
ramcosca@DapperDrake-laptop:~$ sudo apt-get install nessus
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libgdchart-gd2-noxpm libnessus2
Suggested packages:
  nessusd
The following NEW packages will be installed:
  libgdchart-gd2-noxpm libnessus2 nessus
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 356kB of archives.
After unpacking 1004kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
ramcosca@DapperDrake-laptop:~$
```
It's basically aborting when I confirm that I want to do the install, right?

Any help will be appreciated. Thanks.

---

