---
title: "Changing a dual boot os"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by Aflakyan on 2010-10-28
Currently I'm running a dual boot of Ubuntu 10.04 LTS and Windows XP on my laptop. However, lately, I've been playing with a usb portable version of a Debian based os named T(A)ILS (old name Amnesia, I think).

Basically, what I'm trying to figure out is how exactly to go about removing Unbuntu as one of my dual boot operating systems and replacing it with another one without mucking up my XP. 

Any suggestions or redirections would be greatly appreciated.

---

### Post by hhh on 2010-10-28
If you're pretty sure the new OS will install itself and Grub properly, you can just install it right over the Ubuntu partition. I recommend either having an Ubuntu Live CD or burning a copy of SuperGrub Rescue Disk first though, as if the install messes up you can easily restore the Windows Master Boot Record with it and/or then install/reinstall Ubuntu again...
[http://www.supergrubdisk.org/super-grub-disk/](http://www.supergrubdisk.org/super-grub-disk/)

---

### Post by Aflakyan on 2010-10-28
Thanks a ton - I'll give it a shot.

---

