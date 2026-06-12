---
title: "Base-installation death trap"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by Nargile on 2005-05-14
Thread already running in 4.10 forums, but can't hurt putting it here aswell.. Apparantly this is a cross-version problem:

During installation of the base system i get the following error:
The debootstrap program exited with an error (return value 1)
Check /var/log/messages or see virtual console 3 for details.

/var/log/messages show: 
tar: Invalid tar header checksum
tar: Invalid tar magic

Already ran checksum test on the cd and it's correct. Also, my flatmate got the 4.10 install bundled with a pc-magazine so we tried that, but with the exact same error. Tried to read what it did just before it died, and i THINK it was validating passwd(about 20% into installing). It dies at the exact same spot on both install-cd's. It always shows "Invalid tar magic", but about half the time it also shows "Invalid tar herader checksum"

I think it must be a hardware-thing. The computer i'm installing on is a PII-MMX 450 with 128MB RAM, which i'm intending to run as a server for uni-projects. It's been running both slackware and fedora core 3 in the past, which worked well. I also tried running the install with different options(server, custom etc), but nothing helps. ](*,) 

Anyone have the same problem, or a solution it would be greatly appreciated.

---

### Post by alastair on 2005-05-14
There might also be a /var/log/debootstrap.log file worth a look.

Describe you disks/partitions :

 - what disk/size
 - what partitioning / sizes
 - what the mount points are

This is 5.04 (Hoary), yes?

---

