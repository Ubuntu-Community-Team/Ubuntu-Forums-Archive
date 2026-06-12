---
title: "Clutch won't uninstall! Argh!"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by Mizled on 2008-07-09
So...I'm trying to remove clutch but for whatever reason it won't leave. I've tried deleting the dir manually but then it complains that there is no dir to delete. Any suggestions?

```
~$ sudo apt-get -f install
[sudo] password for zane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  clutch
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 815kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115702 files and directories currently installed.)
Removing clutch ...
rm: cannot remove `/usr/share/clutch/www/remote/data': Is a directory
dpkg: error processing clutch (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 clutch
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Mizled on 2008-07-09
Resolved the issue myself.

I did...

```
sudo rm -r /usr/share/clutch/
```

```
sudo apt-get install --reinstall clutch
```

```
sudo apt-get remove clutch
```

---

