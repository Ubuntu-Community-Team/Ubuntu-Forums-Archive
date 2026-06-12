---
title: "Read-only file system after attempted upgrade"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by Japheth on 2010-05-22
I have Ubuntu installed on a VPS and tried upgrading from 9.04 using apt-get dist-upgrade today. Everything was working fine until the system needed to restart. After the restart, I could no longer ssh in, but was able to use an AJAX console on my host's (Linode) site to gain access. Once I got that, I realized the system was read-only. I've found a few solutions for this, but a lot seem to require having direct access to the machine. I also tried running fschk, but that didn't seem to find any errors.

I have the option of reinstalling the OS, but I'd really prefer to at least move all the important files I have there first. Now, I can't ftp or ssh, so I have no easy way of copying stuff from the vps. Any help would be greatly appreciated.

EDIT: After the initial post, I checked the Linode FAQs and discovered a way to boot into Ubuntu from a different partition and gain write access that way. I tried removing the lock files as per [http://georgia.ubuntuforums.org/showthread.php?p=6836462](http://georgia.ubuntuforums.org/showthread.php?p=6836462) and running fsck. The former doesn't help and the latter reports no problems. Any other suggestions would be most welcome.

---

