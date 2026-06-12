---
title: "Fglrx remove problem"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by ZzeCoOl on 2006-06-28
When im tryin to remove fglrx-xorg-driver  this is what i get 


> The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 21.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 124273 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)


and this cannot be solved with th mv libGL.so.1.2 libGL.so.1.2.old trick.

Please help me :(

---

### Post by David Valentine on 2006-06-30
I'm having the exact same problem.  Have you found any answers?

---

