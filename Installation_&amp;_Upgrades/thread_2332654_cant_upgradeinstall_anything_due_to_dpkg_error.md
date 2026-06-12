---
title: "cant upgrade/install anything due to dpkg error"
date: 2016-08-02
forum: Installation &amp; Upgrades
---

### Post by winkeladvokat on 2016-08-02
Hey
Im getting this error wen using ```
apt-get upgrade
```:

```
root@GPR0078:/usr/bin# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
Setting up monitorix (3.8.1-izzy1) ...
chown: cannot access ‘/etc/monitorix/conf.d’: No such file or directory
dpkg: error processing package monitorix (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 monitorix
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@GPR0078:/usr/bin#

```

how can I remove this error? 
sorry but Im relatively new to linux:oops:

---

### Post by Bashing-om on 2016-08-02
winkeladvokat; Hello;

A quick look and I do not see that monitorix is in our software repository .
Where did you get it ..?
Is the package manager tracking this package?
What returns from terminal command:
```

apt-cache policy monitorix

```

[INDENT][INDENT]maybe no fault of 'buntu's
[/INDENT][/INDENT]

---

