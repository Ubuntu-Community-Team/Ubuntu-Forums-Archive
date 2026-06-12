---
title: "Newest kernel fails to boot on Sony Vaio"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by maclover201 on 2008-11-01
Hi-

I just upgraded from Ubuntu 8.04 to Ubuntu 8.10. I am running Ubuntu on a Sony Vaio and am having a problem booting up with the new kernel (version 2.6.27-7).

Whenever it tries to boot up, this is what it says:

ALERT! /dev/disk/by-uuid/487ee3ec-3c8e-47bd-ab0e-40cb3460ddd5 does not exist. Dropping to a shell!
ata2: SRST failed (errno=-16)
ata2: reset failed, giving up

In my /proc/cmdline:

root=UUID=487ee3ec-3c8e-47bd-ab0e-40cb3460ddd5 ro quiet splash

The system starts up fine with kernel version 2.6.24-21, but it doesn't with the new 2.6.27-7. What's going on? Do I need to change my /proc/cmdline to accommodate for the new kernel?

Thanks for your help!

-Morgan

---

### Post by maclover201 on 2008-11-02
:bump:

---

### Post by klanspar on 2008-11-03
Same problem. Any help would be appreciated.

---

### Post by Efros on 2008-11-05
same problem here and not on a Vaio.


Update fixed see [http://ubuntuforums.org/showthread.php?p=6117376#post6117376](http://ubuntuforums.org/showthread.php?p=6117376#post6117376)

---

