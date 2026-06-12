---
title: "Cannot (un)install anything: dpkg error code (1)"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by haseeb on 2010-11-08
I cannot install or uninstall any package or update the os. Anything with apt-get shows the error message like the this -

> xxx@yyy:~$ sudo apt-get autoremove
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 60 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 1: unexpected EOF while looking for matching `"'
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any help?

---

### Post by amauk on 2010-11-08
try
```
sudo apt-get install -f
```

---

### Post by haseeb on 2010-11-09
Thanks. But no use of it. Got the same error.

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 60 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 1: unexpected EOF while looking for matching `"'
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by haseeb on 2010-11-09
found a thread [here]("http://ubuntuforums.org/showthread.php?t=1578263"),

the solution from [drs305]("http://ubuntuforums.org/member.php?u=223945") solved the problem.

for reference i am also pasting his solution here,
```

sudo mv /var/lib/dpkg/info/install-info.postinst /var/lib/dpkg/info/install-info.postinst.bad
```

to undo,

```
sudo mv /var/lib/dpkg/info/install-info.postinst.bad /var/lib/dpkg/info/install-info.postinst
```

---

### Post by mörgæs on 2010-11-09
Good, please mark the thread 'solved' using 'thread tools'.

---

