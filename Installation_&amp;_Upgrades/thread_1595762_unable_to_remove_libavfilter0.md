---
title: "unable to remove libavfilter0"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by kiddykoff on 2010-10-13
I upgraded from 10.04 to 10.10 and one of my packages, libavfilter0 was unabled to be uninstalled. somewhere along the line i tried the command, sudo apt-get install -f and sudo apt-get remove libavfilter0. Both give the same result.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libavfilter0
0 upgraded, 0 newly installed, 1 to remove and 1105 not upgraded.
1 not fully installed or removed.
After this operation, 127kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 217973 files and directories currently installed.)
Removing libavfilter0 ...
dpkg (subprocess): unable to execute installed post-removal script (/var/lib/dpkg/info/libavfilter0.postrm): Exec format error
dpkg: error processing libavfilter0 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libavfilter0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

as you can see there's an error in removing it and this is preventing me from upgrading many packages.

does anyone have any recommendations for removing so i can continue my upgrade to 10.10?

---

### Post by kiddykoff on 2010-10-13
I tried the instructions in this post. but instead deleting files and lines that begin with libavfilter0

[http://ubuntuforums.org/showpost.php?p=9880309&postcount=5](http://ubuntuforums.org/showpost.php?p=9880309&postcount=5)

running sudo apt-get upgrade at the moment. Things are looking better.

---

### Post by kiddykoff on 2010-10-14
i had to re-download the packages because i used sudo apt-get clean earlier, so it took a while. Now i'm back and upgraded to 10.10. feels good man.

---

