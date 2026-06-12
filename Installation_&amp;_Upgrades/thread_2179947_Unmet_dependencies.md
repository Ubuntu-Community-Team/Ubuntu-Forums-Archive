---
title: "Unmet dependencies"
date: 2013-10-10
forum: Installation &amp; Upgrades
---

### Post by Gostling on 2013-10-10
hi, i am install this evening one lib (libmysqlclient15off_5.0.96-0ubuntu3_amd64.deb) after this installation does not seem to do anything, because I get always this error for any installation.

if i try to install mysql:
```
root@ts:~# sudo apt-get install mysql-server mysql-clientReading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libmysqlclient15off : Depends: mysql-common (>= 5.0.96-0ubuntu3) but it is not going to be installed
 mysql-client : Depends: mysql-client-5.5 but it is not going to be installed
 mysql-server : Depends: mysql-server-5.5 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

ty for help

---

### Post by ian-weisser on 2013-10-11
What version of Ubuntu are you running?
mysql-client 5.0 versions have been long superseded. The current version is 5.5

Where did you get libmysqlclient15off_5.0.96-0ubuntu3_amd64.deb from?
I do not see it in the Ubuntu repositories.
I do not see a dependency of mysql-client by that name.

---

### Post by mörgæs on 2013-10-11
I noticed you are using the root account. This might be worth reading:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

