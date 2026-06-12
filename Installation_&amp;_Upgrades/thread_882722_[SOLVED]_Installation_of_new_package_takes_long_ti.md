---
title: "[SOLVED] Installation of new package takes long time and freezes the system until com"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by amitst on 2008-08-07
Whenever I try to install a new package, the system takes at least 10 minutes to configure it (leaving aside the download time). For e.g. the configuration of the CHM file viewer took me more than 10 minutes. Worst still, it nearly freezes the system during the installation process (the hard disk works like crazy during the configuration step). I have been installing the similar packages on a laptop with a lower hardware configuration and I haven't seen this issue there.

Ubuntu version: Hardy Heron

uname -a output

Linux amit-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

Any tips?

---

### Post by wpshooter on 2008-08-07
I think I would first try doing an:  apt-get clean

And then run a forced check of the disk.

---

### Post by amitst on 2008-08-08
I did apt-get clean. However when I tried disk check it gave me the following warning,

```

$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.

```

Do I have to run this command from a livecd?

Yeah, and I am experiencing quite frequent power outages nowadays, so many times the system doesn't shutdown cleanly.

Thanks,
Amit

---

### Post by amitst on 2008-08-12
Looks like "sudo apt-get clean" has resolved the issue.

---

