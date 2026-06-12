---
title: "Problems with vmware due to uuid and dev changing"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by arobinson on 2008-08-24
I have gotten my Dual boot windows machine to work inside VMWare on XUbuntu hardy using a Raw disk. The problem is that the VMDK file format does not allow me to use a soft link to set the raw disk to use. I have two drives a SATA drive that is my Ubuntu disk and an IDE drive that is my windows disk. Being a Ubuntu user, I am using grub. The problem is that the device names change on me! 

/dev/sda is sometimes the SATA drive and other times the IDE drive!

While this does not affect linux as I have everything using UUID references, I don't see any documentation on the vmdk file format and the usage of UUID identifiers. Right now it looks like this:
```
RW 398297088 FLAT "/dev/sda" 0

```

I tried using the "/dev/disk/by-uuid/..." but VMWare told me this was not a valid device.

How can I get a constant device node for the vmdk to use and be sure it will not change when I reboot?

Thanks,
Andrew

---

