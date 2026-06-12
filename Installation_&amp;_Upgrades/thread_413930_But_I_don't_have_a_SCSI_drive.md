---
title: "But I don't have a SCSI drive"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by kpjoyce on 2007-04-19
For some reason, my 7.04 install CD thinks that my IDE hard drive is a SCSI hard drive. 

How can I convince it otherwise before installing?

Thanks for any help.

---

### Post by Rui Pais on 2007-04-19
> **kpjoyce said:**
> For some reason, my 7.04 install CD thinks that my IDE hard drive is a SCSI hard drive. 

How can I convince it otherwise before installing?

Thanks for any help.

Thats because the new kernels (that came with ubuntu or other distros) use new driver to deal with both PATA and SATA drivers. 

Thats exactly whats expected, although its a bit annoying.

If you have any problem, you need to change /dev/hdXX references on grub menu.lst and fstab to the correspondent UUID.

---

### Post by aircoupe on 2007-04-19
Same here, worked fine with Fiesty Beta, but  now fails to partition during install with the release of 7.04:confused:

---

