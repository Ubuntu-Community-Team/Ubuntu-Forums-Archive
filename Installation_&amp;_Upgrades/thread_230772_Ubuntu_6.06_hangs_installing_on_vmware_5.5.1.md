---
title: "Ubuntu 6.06 hangs installing on vmware 5.5.1"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by jmalbarran on 2006-08-06
Hi,

I'm trying to install Ubuntu 6.06 from live CD and install, in a Virtual Machine from vmware 5.5.1

The Live CD starts OK, and I get the gnome desktop. I select the install icon, and do the partitions, and introduce the login, time, language and keyboard data.

It does the partition and formatting, and begin to copy files. But, at 71% it stops, and hangs the desktop.

I'have tried

- Setting the VM to Ubuntu and to Other 2.6 Kernel
- Using IDE and SCSI virtual hard disk
- Setting acpi=off at start of live CD

I've seen in other threads it happens with low memory or disk in VM, but I setted it to

- Memory: 512Mb
- Disk
  - 1 of 8Gb partitioned as ext3
  - 1 of 512Mb partitioned as swap


Any ideas? How can I see what it's doing the installation program at 71%?

JoseManuel

---

