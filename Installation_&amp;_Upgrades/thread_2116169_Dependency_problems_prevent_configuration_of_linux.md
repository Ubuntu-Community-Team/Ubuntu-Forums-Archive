---
title: "Dependency problems prevent configuration of linux-server"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by timefortea on 2013-02-15
Hi all,
I've been trying to install some additional packages on my Ubuntu Server 12.04 home server but it seems that the dependencies with the linux-server and linux-image-server meta packages have got a bit screwed up. I haven't done anything unusual since the machine was setup, just the odd upgrade to the latest packages. Basically when I try to install or upgrade any packages apt complains because linux-server and linux-image-server seem to be out of sync but I am not sure how to resolve it. Here is some info on the problem and what versions the packages are:

Any example of what I see what I try to install a new package:

```
$ sudo apt-get install python-cheetah
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-server : Depends: linux-image-server (= 3.2.0.32.35) but 3.2.0.37.45 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Info about my system:

```
$ uname -a
Linux tranquil 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

```
$ sudo apt-get -f install
...
The following extra packages will be installed:
  linux-server
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
1 not fully installed or removed.
...
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.32.35); however:
  Version of linux-image-server on system is 3.2.0.37.45.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
 Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
$ dpkg-query -s linux-server
Package: linux-server
Status: install ok unpacked
Version: 3.2.0.32.35
Config-Version: 3.2.0.25.27
Depends: linux-image-server (= 3.2.0.32.35)

```

```
$ dpkg-query -s linux-image-server
Package: linux-image-server
Status: install ok installed
Version: 3.2.0.37.45
Depends: linux-image-3.2.0-37-generic, linux-firmware

```

Any ideas what I should try next?

---

### Post by schragge on 2013-02-15
Do what it suggests
```
sudo apt-get -f install
```

---

### Post by timefortea on 2013-02-15
I did and the results of that are in the third code snippet in my original post. So the question is what I should try next.

---

### Post by schragge on 2013-02-15
Ah sorry, didn't noticed. Well, then try
```

sudo apt-mark manual linux-image-server
sudo apt-get -f remove linux-server

```

---

### Post by timefortea on 2013-02-17
Ah ok I see now - so I forced a remove and then re-installed the latest version and that seems to have done the trick. Thanks for the help!

---

