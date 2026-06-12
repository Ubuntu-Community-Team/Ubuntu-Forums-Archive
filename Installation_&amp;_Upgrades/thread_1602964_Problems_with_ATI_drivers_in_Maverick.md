---
title: "Problems with ATI drivers in Maverick"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by IronLeo on 2010-10-22
Hi! I upgraded my Ubuntu to the last version but when it starts there is only a scratch screen! If I boot the low graphic mode, it gives me the following error (also when I try to remove fglrx) whatever I do in the shell:

```

Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```If I boot linux 2.6.32.25 there is no problem with graphics but I still have that error. Can you help me? Thanks!

---

### Post by IronLeo on 2010-10-22
I solved using 

```

sudo dpkg-divert --remove /usr/lib32/libGL.so.1.2

```

:-)

---

### Post by IronLeo on 2010-10-22
double

---

### Post by IronLeo on 2010-10-22
triple

---

