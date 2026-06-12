---
title: "Yaboot continues to fail to install, not sure why"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by surenot on 2013-02-14
I am trying to install Ubuntu on an old iBook using the alternative installation disk.  The whole installation process goes pretty well until it gets to the part where it installs /etc/yaboot.conf, and it gives me an error message saying that 'Yaboot could not be installed'.  I have tried reformatting the boot partitions which didn't help, reinstalling the system twice (which took a very long time), and using yaboot that came on the CD to try and boot into the installation.  Nothing works.  The closest I have come to a solution is I got a message about how the target kernel is /boot/vmlinux, the parition is /dev/sda3, and the argument is root=/dev/sda3, but I'm not sure how to enter those in the command line to get it to boot that.

I have so far left the partition /dev/sda1 (the Apple partition map) untouched; should I be doing something with that also?  If it helps I have completely wiped the hard drive of the Mac OSX that was on there.

---

