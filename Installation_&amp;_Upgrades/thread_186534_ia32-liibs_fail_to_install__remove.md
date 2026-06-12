---
title: "ia32-liibs fail to install / remove"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by almark on 2006-06-02
Trying to install / reinstall ia32-libs:

mark@ubuntu:~ $ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  ia32-libs
1 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/3837kB of archives.
After unpacking 14.0MB disk space will be freed.
Selecting previously deselected package ia32-libs.
(Reading database ... 125346 files and directories currently installed.)
Preparing to replace ia32-libs 1.4ubuntu4 (using .../ia32-libs_1.4ubuntu19_amd64.deb) ...
dpkg-divert: rename involves overwriting `/usr/bin/ldd' with
  different file `/usr/bin/ldd.amd64', not allowed
dpkg: error processing /var/cache/apt/archives/ia32-libs_1.4ubuntu19_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.4ubuntu19_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Trying to remove ia32-libs:

mark@ubuntu:~ $ sudo dpkg --remove ia32-libs 
Password:
(Reading database ... 125345 files and directories currently installed.)
Removing ia32-libs ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/bin/ldd to /usr/bin/ldd.ia32-libs by ia32-libs'
  found `diversion of /usr/bin/ldd to /usr/bin/ldd.amd64 by ia32-libs'
dpkg: error processing ia32-libs (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 ia32-libs

What's going on and how do I fix this?

Regards
Mark

---

### Post by DerManoMann on 2006-06-10
I manually renamed /usr/bin/ldd - that was enough. 
e.g: sudo mv /usr/bin/ldd /usr/bin/ldd.old

After that sudo apt-get install -f worked fine

Cheers, mano

---

### Post by John Jason Jordan on 2006-06-19
[QUOTE=DerManoMann]I manually renamed /usr/bin/ldd - that was enough. 
e.g: sudo mv /usr/bin/ldd /usr/bin/ldd.old
After that sudo apt-get install -f worked fine[/QUOTE]
I just tried that, but it didn't help. Still can't fix ia32-libs. All I get is:

jjj@Devil5:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ia32-libs
0 upgraded, 0 newly installed, 1 to remove and 92 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 23.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 166346 files and directories currently installed.)
Removing ia32-libs ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/bin/ldd to /usr/bin/ldd.ia32-libs by ia32-libs'
  found `diversion of /usr/bin/ldd to /usr/bin/ldd.amd64 by ia32-libs'
dpkg: error processing ia32-libs (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 ia32-libs
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zorzi on 2006-06-22
This is how I got around the problem. Two files come into play /usr/bin/ldd (this seems to come from an older version of glibc) and /usr/bin/ldd.amd64 (this is a dpkg-diversion of the current /usr/bin/ldd.amd64). I have moved /usr/bin/ldd to some other place so that following command proceeds without errors:
 'sudo dpkg-divert --rename --remove /usr/bin/ldd.amd64'.

After that ia32-lib installed without problems.

With regards to your problems, try to experiment a bit dpkg-divert, there are some examples in the man pages. Interesting outputs for you might be 'dpkg -S /usr/bin/ldd' and 'dpkg-divert --list /usr/bin/ldd'.

---

