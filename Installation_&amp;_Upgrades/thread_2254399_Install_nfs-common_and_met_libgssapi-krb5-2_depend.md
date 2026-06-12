---
title: "Install nfs-common and met libgssapi-krb5-2 dependency issue"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by jason148 on 2014-11-26
Hi All,


I'm trying to install nfs client in Ubuntu 14.04 trusty with apt-get install and met the dependency issue of libgssapi-krb5-2:




```
root@test:~# apt-get install nfs-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libgssapi-krb5-2 : Depends: libkrb5-3 (= 1.12.1+dfsg-15) but 1.12+dfsg-2ubuntu4 is to be installed
 nfs-common : Depends: libgssglue1 but it is not going to be installed
              Depends: libnfsidmap2 but it is not going to be installed
              Depends: libtirpc1 but it is not going to be installed
              Depends: rpcbind (>= 0.2.0-6ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


Then I tried to apt-get update, after that execute apt-get upgrade&#65292;the issue still exist:


```
root@test:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libgssapi-krb5-2 : Depends: libkrb5-3 (= 1.12.1+dfsg-15) but 1.12+dfsg-2ubuntu4 is installed
E: Unmet dependencies. Try using -f.

```



So I tried to install libkrb5-3, and issue was still there:


```
root@test:~# apt-get install -f libkrb5-3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libgssapi-krb5-2 : Depends: libkrb5-3 (= 1.12.1+dfsg-15) but 1.12+dfsg-2ubuntu4.2 is to be installed
 libkrb5-3 : Depends: libkrb5support0 (= 1.12+dfsg-2ubuntu4.2) but 1.12+dfsg-2ubuntu4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```



Then I checked the /etc/apt/sources.list, it hasn't been modified before:


```
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
........

```

I can only download libkrb5-3 (1.12.1+dfsg-15) deb and install manually? I googled and only find its source package. 
Any ideas?

Thanks in advance.

---

