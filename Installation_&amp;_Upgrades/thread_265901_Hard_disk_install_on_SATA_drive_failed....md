---
title: "Hard disk install on SATA drive failed..."
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by simonbr on 2006-09-26
Hi, 

This problem is already solved, but others may run into it as well.

I wanted to install Ubuntu 6.0.6 on a SATA drive. The BIOS was set to boot from *this* drive, although the system also has an IDE drive in it. 

The installation went fine, but the PC would not boot from hard disk. Booting from the CDROM again, I could mount the SATA drive and see the root directories on it. 

In the end I removed the IDE drive and installed again; this worked! I think the first time around, some parts of the boot software were installed on the IDE drive, maybe assuming the system would boot from that drive even if this was not the case at all. It may be a good idea to fix this in the next version. 

Best regards, 
Simon Brouwer.

---

### Post by confused57 on 2006-09-26
You're right, grub was probably installed on the IDE drive...it seems to be a common problem, when there is a combination of SATA and IDE drives, Ubuntu usually installs grub to the IDE drive regardless of which drive Ubuntu was installed on.
Good job figuring it out on your own... it'll probably get fixed in future Ubuntu versions.

---

### Post by pseudonym on 2006-09-26
It's been an issue with libata, the linux SATA driver, for quite a while now. See [http://linux-ata.org/](http://linux-ata.org/) .

---

