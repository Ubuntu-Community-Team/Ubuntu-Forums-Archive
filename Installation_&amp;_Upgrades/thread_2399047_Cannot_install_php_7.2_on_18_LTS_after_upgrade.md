---
title: "Cannot install php 7.2 on 18 LTS after upgrade"
date: 2018-08-21
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2018-08-21
After upgrading from 16 LTS to 18 LTS I cannot upgrade/install the latest version of php, which I believe is 7.2

I get the following error

```
sudo apt-get install php7.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package php7.2
E: Couldn't find any package by glob 'php7.2'
E: Couldn't find any package by regex 'php7.2'

```

---

### Post by LHammonds on 2018-08-21
#1 - Output what version you are currently running:

```
lsb_release -a
uname -a
```

#2 - Check which repositories you are pointed to.  Look in /etc/apt/sources.list and /etc/apt/sources.list.d

The uncommented lines in my sources.list:
```

deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb [arch=amd64] http://mirror.nodesdirect.com/mariadb/repo/10.3/ubuntu bionic main

```

There is nothing in my sources.list.d folder.

```

root@srv-franknbeans# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic
root@srv-franknbeans:/# uname -a
Linux srv-franknbeans 4.15.0-32-generic #35-Ubuntu SMP Fri Aug 10 17:58:07 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by lister171254 on 2018-08-21
```
llist@vps01:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic
```

```
llist@vps01:~$ uname -a
Linux vps01 4.15.0-32-generic #35-Ubuntu SMP Fri Aug 10 17:58:07 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

/etc/apt/resources.list looks like this
```
deb http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial main restricted
deb-src http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial main restricted

deb http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial-updates main restricted
deb-src http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial-updates main restricted

deb http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial universe
deb-src http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial universe
deb http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial-updates universe
deb-src http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial-updates universe

deb http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial multiverse
deb-src http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial multiverse
deb http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial-updates multiverse
deb-src http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial-updates multiverse

deb http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial-backports main restricted universe multiverse
deb-src http://ubuntu.mirror.digitalpacific.com.au/archive/ xenial-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```

There is nothing in /etc/apt/resources.list.d

---

### Post by LHammonds on 2018-08-21
Notice the problem yet?

**EDIT:**

xenial = 16.04 repo
bionic = 18.04 repo

Your in-place upgrade apparently did not update everything correctly.  Maybe due to incorrect file permissions or a bug in the script.

You can get around this issue right now by removing the lines in your apt list file and making them match what I posted.

Then issue an apt-get update, then apt-get upgrade

However, I would not trust this system and would be considering building a fresh 18.04 system from scratch and install the applications and configure it to run like your old server.  Then migrate the data over and swap the IP addresses so you can run on a server that was configured for and as 18.04 without any potential issues getting in your way from prior upgrade paths.

I only upgrade to new versions by installing them from scratch and migrating the data over from the old system once I document and verify everything works as it is supposed to.  The issue you are having just re-affirms that the extra steps I take are the best way (for me...since I never want to experience any downtime due to unforeseen upgrade issues)

LHammonds

---

### Post by lister171254 on 2018-08-27
Thanks for findin the problem.
All ok now

---

