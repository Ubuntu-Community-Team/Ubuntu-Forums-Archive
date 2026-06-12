---
title: "Bionic upgrade"
date: 2018-09-06
forum: Installation &amp; Upgrades
---

### Post by polymorphic.dk on 2018-09-06
I get this in my motd after doing a release upgrade from 16.04 lts to 18.04 lts:


```
0 packages can be updated.
0 updates are security updates.


You have packages from the Hardware Enablement Stack (HWE) installed that
are going out of support on 2023-04-30.


To upgrade to a supported (or longer-supported) configuration:


* Upgrade from Ubuntu 16.04 LTS to Ubuntu 18.04 LTS by running:
sudo do-release-upgrade -p


OR


* Switch to the current security-supported stack by running:
sudo apt-get install linux-generic-hwe-18.04


and reboot your system.

```

Therefore i did:
```
js@host:~$ sudo do-release-upgrade -p
Checking for a new Ubuntu release
No new release found.

```

And then:


```
js@host:~$ sudo apt-get install linux-generic-hwe-18.04
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-generic-hwe-18.04
E: Couldn't find any package by glob 'linux-generic-hwe-18.04'
E: Couldn't find any package by regex 'linux-generic-hwe-18.04'


```

```

js@host:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic

```

What is going on here?

Thanks in advance for any help on this.

---

### Post by dsstorefile1 on 2018-09-06
The message is probably ahead of its time as the package doesn't exist yet: [https://packages.ubuntu.com/search?keywords=linux-generic-hwe-&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=linux-generic-hwe-&searchon=names&suite=all&section=all)

---

