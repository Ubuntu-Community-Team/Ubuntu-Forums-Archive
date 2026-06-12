---
title: "[B]Help LILO Problems!![/B]"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by hempa on 2007-02-11
Im trying to change from grub to LILO and when i type the, sudo liloconfig command in the terminal I get this 

ubuntu@ubuntu:~$ sudo liloconfig
LILO, the LInux LOader, sets up your system to boot Linux directly
from your hard disk, without the need for a boot floppy.

    WARNING!
        Your /etc/fstab configuration file gives device unionfs as the root
        filesystem device. This doesn't look to me like an "ordinary" block
device. Either your fstab is broken and you should fix it, or you are
using hardware (such as a RAID array) which this simple configuration
program does not handle.

You should either repair the situation or hand-roll your own
/etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
again to retry the configuration process.
Documentation for LILO can be found in /usr/share/doc/lilo/.

How can i go on from this point Please help!!

---

