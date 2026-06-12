---
title: "Apparmor issue after Upgrade from 12.04 to 14.04"
date: 2015-08-13
forum: Installation &amp; Upgrades
---

### Post by seanmancini2010 on 2015-08-13
Hey All,

I am having a issue with apparmor since I did an upgrade from 12.04 to 14.04

Everything else is working fine but Apparmor wont load

See below



:~$ sudo modprobe apparmor
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/4.1.0-x86_64-linode59/modules.dep.bin'

sudo apparmor_status
apparmor module is not loaded

 uname -a
Linux blog 4.1.0-x86_64-linode59 #1 SMP Mon Jun 22 10:39:23 EDT 2015 x86_64 x86_64 x86_64 GNU/Linux
sean@blog:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty



Any ideas ?

I have reinstalled apparmor and purged all previous settings 

Any help would be awesome

---

### Post by seanmancini2010 on 2015-08-13
Should I post this in another section ?

---

### Post by QIII on 2015-08-13
Well,  I had removed your previous post so that your question would get back in the unanswered posts query.

This is a perfectly good place to post.  But you might be patient and allow the volunteers here -- from all over the world and every time zone -- to see your question.

Please wait about 12 hours before bumping again.

---

### Post by seanmancini2010 on 2015-08-14
Bump

---

