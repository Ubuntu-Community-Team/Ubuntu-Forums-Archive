---
title: "Broken Package - ia32-libs"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2006-06-19
Upgrade from Breezy-64 to Dapper-64 was problematic. I finally got everything fixed except OpenOffice.org. And the problem is ia32-libs. Synaptic says it is broken, but nothing I have tried has fixed it. I can't remove it, reinstall it, upgrade it or anything. It just sits there broken, grinning at me, daring me to try to remove it. The little bastard.

I've read through these forums and found a few references to it, but either the solution someone else used didn't work for me, or I couldn't figure what they did.

---

### Post by John Jason Jordan on 2006-06-19
As additional information, I tried the following from the command line:

jjj@Devil5:~$ sudo apt-get -f remove
Password:
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
jjj@Devil5:~$

I don't know what those error messages mean. I hope someone else does so I can get this fixed.

---

