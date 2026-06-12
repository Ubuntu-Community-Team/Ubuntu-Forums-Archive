---
title: "[Ubuntu] dpkg: error processing libtxc-dxtn-s2tc0:i386 (--configure)"
date: 2013-12-30
forum: Installation &amp; Upgrades
---

### Post by yaayaawar on 2013-12-30
While upgrading from 13.10 to 14.04 via upgrade manager, I encountered a problem and upgrade stopped suddenly.
Later, it started showing:

Setting up libtxc-dxtn-s2tc0:i386 (0~git20131104-1) ...
update-alternatives: error: alternative path /usr/lib/x86_64-linux-gnu/libtxc_dxtn_s2tc.so.0 doesn't exist
dpkg: error processing libtxc-dxtn-s2tc0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libtxc-dxtn-s2tc0:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)


Plz help me. I am almost new user.

Vivek

---

### Post by yaayaawar on 2013-12-30
**sudo dpkg --configure -a**
Setting up libtxc-dxtn-s2tc0:i386 (0~git20131104-1) ...
update-alternatives: error: alternative path /usr/lib/x86_64-linux-gnu/libtxc_dxtn_s2tc.so.0 doesn't exist
dpkg: error processing libtxc-dxtn-s2tc0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libtxc-dxtn-s2tc0:i386
 

**sudo apt-get install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up libtxc-dxtn-s2tc0:i386 (0~git20131104-1) ...
update-alternatives: error: alternative path /usr/lib/x86_64-linux-gnu/libtxc_dxtn_s2tc.so.0 doesn't exist
dpkg: error processing libtxc-dxtn-s2tc0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libtxc-dxtn-s2tc0:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by yaayaawar on 2013-12-30
I got this: [http://anonscm.debian.org/gitweb/?p=collab-maint/s2tc.git;a=commitdiff;h=f5b86b91bf864c7cfdee73d844ca78c5f19c6412](http://anonscm.debian.org/gitweb/?p=collab-maint/s2tc.git;a=commitdiff;h=f5b86b91bf864c7cfdee73d844ca78c5f19c6412)

but I don't understand a bit.

Vivek

---

