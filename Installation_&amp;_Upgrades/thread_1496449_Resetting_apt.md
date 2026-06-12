---
title: "Resetting apt?"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by DeltaZero on 2010-05-29
One of the packages I tried to remove has failed:

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
A package failed to install.  Trying to recover:
```

Now this removal is stuck in the apt queue and I cannot unmark it or do anything else. It is still there even after the restart. My package manager no longer works, because it always does removals first, and this removal always fails aborting anything else I am trying to do.
What can I do?

---

### Post by Soul-Sing on 2010-05-29
an other one: [http://ubuntuforums.org/showthread.php?t=1488878](http://ubuntuforums.org/showthread.php?t=1488878)
maybe the solutions in that thread will help you?

---

### Post by DeltaZero on 2010-05-29
Thanks, I've removed the files so that the removal passed.
Really annoying though.

---

