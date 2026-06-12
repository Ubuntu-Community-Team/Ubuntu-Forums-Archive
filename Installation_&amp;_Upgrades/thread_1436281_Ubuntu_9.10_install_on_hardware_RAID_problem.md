---
title: "Ubuntu 9.10 install on hardware RAID problem"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by ismooth on 2010-03-22
I'm trying to install Ubuntu 9.10 on a server machine with hardware raid (raid 1).
I downloaded Alternate CD, but was unable to install it. here is more info...

when computer was connected to internet:
I got following error: "Debootstrap warning   file:///cdrom/pool/main/libt/libtext-iconv-perl/libtext-iconv-perl_1.7-1build1_i386.deb was corrupt"
i pressed continue i got error: "Couldn't download package libtext-iconv-perl"
then the step Install base system stops, and I can try to run that step again. then i got following error: "Failure to run: chroot /target dpkg --force-depends --install /var/cache/apt/archives/libc6_2.10.1-0ubuntu15_i386.deb"

in /var/log/syslog I found this (among many other lines):
debootstrap: A non-dpkg owned copy of the libc6-i686 package was found.

then i disconnected from internet...
i got following error:  Debootstrap warning: file:///cdrom/pool/main/m/mawk/mawk_1.3.3-15ubuntu1_i386.deb was corrupt

one time installer asked me for ubuntu 9.10 install cd, but it wouldn't do anything with it. (i don't remember exactly, i couldn't reproduce this scenario again)

what can I do to install it on the server?

---

### Post by dstew on 2010-03-23
Are you sure the CD is OK? Does it install OK on other machines?

---

### Post by ismooth on 2010-03-30
I tried with several CDs, different Ubuntu versions, but in the end working combination was to create raid arrays with alternate CD, stop installation, reboot the machine, and do the install with Desktop CD  (although it didn't work from first try...got errors around 77% of progress at first).

Tnx anyway!

---

