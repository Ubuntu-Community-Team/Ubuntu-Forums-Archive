---
title: "apt-get gives a segmentation fault"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by wickett on 2010-07-16
I found the answer here: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2387248.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2387248.html)

```
ubuntu@localhost:/var/log$ sudo apt-get remove sleuthkit
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  sleuthkit
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
After this operation, 5,267kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 31365 files and directories currently installed.)
Removing sleuthkit ...
Processing triggers for man-db ...
Segmentation fault
```

Turns out that if the /var/log/apt directory is missing then this wont work.  I was able to get this working again with a 

```
sudo mkdir /var/log/apt
```

---

