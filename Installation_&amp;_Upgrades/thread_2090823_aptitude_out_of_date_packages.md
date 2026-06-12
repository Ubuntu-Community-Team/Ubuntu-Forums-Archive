---
title: "aptitude out of date packages"
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by tiberiup on 2012-12-03
Hi, i have ubuntu server 11.04 and i installed apache2 server with aptitude, the version installed is very old apache 2.2.17 ( 2010 )
```

root@ubuntu:/etc# apt-get install apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/1,480 B of archives.
After this operation, 36.9 kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 35353 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.17-1ubuntu1.5_i386.deb) ...
Setting up apache2 (2.2.17-1ubuntu1.5) ...

```

I think is installed from an archive out of date, how can i update this to have all version up to date ?

---

### Post by ibjsb4 on 2012-12-03
Yep, 11o4 has reached EOL and no longer supported through regular update channels. It would be better to use 12.04 which will be supported for five years.

---

### Post by tiberiup on 2012-12-03
it's no possible to somehow update repository or something ? soon i will manage a dedicated server with ubuntu 11.04 the web host offer only that version of ubuntu on the dedicated server that i will choose...

i tried to manual install apache but it was not so good :)

---

