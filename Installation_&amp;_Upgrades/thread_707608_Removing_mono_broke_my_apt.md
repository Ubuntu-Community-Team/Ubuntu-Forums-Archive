---
title: "Removing mono broke my apt"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by JC Denton on 2008-02-25
Hello All

I recently attempted to install the latest version of mono by following this guide:


[http://blog.ruski.co.za/page/Install...buntu-710.aspx](http://blog.ruski.co.za/page/Install...buntu-710.aspx)

However, somewhere along the line I messed up ($ apt-get remove mono-common ) and apt/synaptic refuse to run. The errors returned are (trying to reinstall):

```

apt-get install mono-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  monodoc-manual libfbclient1 libikvm-native firebird1.5-common libnunit-doc
  libgdiplus
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  f-spot monodevelop tomboy
The following NEW packages will be installed:
  mono-common
0 upgraded, 1 newly installed, 3 to remove and 82 not upgraded.
3 not fully installed or removed.
Need to get 0B/109kB of archives.
After unpacking 22.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 222500 files and directories currently installed.)
Removing f-spot ...
scrollkeeper-update: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing f-spot (--remove):
 subprocess post-removal script returned error exit status 127
Removing monodevelop ...
update-mime-database: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing monodevelop (--remove):
 subprocess post-removal script returned error exit status 127
Removing tomboy ...
scrollkeeper-update: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing tomboy (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 f-spot
 monodevelop
 tomboy
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Erinyes:/home/fabian# sudo apt-get install --reinstall mono-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  monodoc-manual libfbclient1 libikvm-native firebird1.5-common libnunit-doc
  libgdiplus
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  f-spot monodevelop tomboy
The following NEW packages will be installed:
  mono-common
0 upgraded, 1 newly installed, 3 to remove and 82 not upgraded.
3 not fully installed or removed.
Need to get 0B/109kB of archives.
After unpacking 22.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 222500 files and directories currently installed.)
Removing f-spot ...
scrollkeeper-update: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing f-spot (--remove):
 subprocess post-removal script returned error exit status 127
Removing monodevelop ...
update-mime-database: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing monodevelop (--remove):
 subprocess post-removal script returned error exit status 127
Removing tomboy ...
scrollkeeper-update: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing tomboy (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 f-spot
 monodevelop
 tomboy
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm guessing apt maintains a list somewhere with jobs left to run like removing my apps dependent on mono. Is there not a way to temporarily remove these from it's tasks/'to do' list, reinstall mono and have it run properly again?

---

