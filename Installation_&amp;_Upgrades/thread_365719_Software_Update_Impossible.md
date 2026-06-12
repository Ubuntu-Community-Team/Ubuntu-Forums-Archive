---
title: "Software Update Impossible"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by intuitivesoul on 2007-02-20
Hey All,

Software update impossible, says the update manager.
Suggests using synaptic or run the command, for which the output is as follows.
How do i get it fixed ?

> sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  graphviz-cairo
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  graphviz-cairo
0 upgraded, 0 newly installed, 1 to remove and 28 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 193kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 171739 files and directories currently installed.)
Removing graphviz-cairo ...
/var/lib/dpkg/info/graphviz-cairo.postrm: 11: dot: not found
dpkg: error processing graphviz-cairo (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)

~ Soul

---

### Post by dcstar on 2007-02-20
> **intuitivesoul said:**
> Hey All,

Software update impossible, says the update manager.
Suggests using synaptic or run the command, for which the output is as follows.
How do i get it fixed ?

> sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  graphviz-cairo
Use '**apt-get autoremove**' to remove them.
The following packages will be REMOVED:
  graphviz-cairo
0 upgraded, 0 newly installed, 1 to remove and 28 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 193kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 171739 files and directories currently installed.)
Removing graphviz-cairo ...
/var/lib/dpkg/info/graphviz-cairo.postrm: 11: dot: not found
dpkg: error processing graphviz-cairo (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)

~ Soul

Shut down Synaptic, open a terminal and:
```
**sudo apt-get autoremove**
```

---

### Post by xoan on 2007-03-22
You need `graphviz' package, so install it. Apt-get couldn't install automatically, so:

```
$ sudo apt-get install -d graphviz
$ sudo dpkg -i /var/cache/apt/archives/graphviz_2.8-2.1ubuntu1_i386.deb
$ sudo apt-get autoremove --purge
```

`graphviz' package provides /usr/bin/dot that is necessary for to remove `graphviz-cairo'.

---

### Post by mardawi on 2007-03-28
Hi,

This is the second time i face this problem and this post saves me :) 

i will really appreciate it if you could explain why this problem is happening and what these 3 commands are doing to fix it

thanks a lot!

---

