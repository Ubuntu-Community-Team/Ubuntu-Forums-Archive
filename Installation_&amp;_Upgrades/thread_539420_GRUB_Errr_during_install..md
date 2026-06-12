---
title: "GRUB Errr during install."
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by Thesus on 2007-08-31
Okay, during my install of ubuntu (on an hp laptop that already has windows vista on it and had some issues when trying to set up the partitions), once I get through the wizard and the system actually starts installing, I've twice received this error:

"Executing 'grub-install (hd0)' failed.

This is a fatal error."

It doesn't present any options to fix, just 'ok', which ends the install process. Help?

Edit: Oops, bad typo in the subject line, sorry.

---

### Post by Pumalite on 2007-08-31
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) Examine your partitions and report back.
If not; use rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by Thesus on 2007-08-31
GParted isn't being nice.

ubuntu@ubuntu:~/Desktop/gparted-0.3.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
ubuntu@ubuntu:~/Desktop/gparted-0.3.3$ 

Anyway, I have to go to work, so I'll check later.

---

### Post by Pumalite on 2007-08-31
You have to download the iso from the link I gave you, burn to a CD and boot from it.

---

