---
title: "getting ubuntu to work through freebsd's bootloader"
date: 2006-03-16
forum: Installation &amp; Upgrades
---

### Post by dninja on 2006-03-16
I've got FreeBSD 6 on my machine and have just installed ubuntu. It installed grub which then failed to boot with error 18. The standard fix for this is to move the boot partition closer to the start of the drive which I can't do as everything else on the machine is setup and happy where it is.

So I want to keep using the FreeBSD bootloader. I got it back on with a bsd live cd and now it gives me the option to boot linux but then hangs. I've seen other posts about this happening with most people desparate to reinstall grub or lilo. I don't want to/can't do this I want to keep the bsd bootloader.

Can anyone tell me why the boot is locking up when I select linux. I don't even see a grub menu or comment so I'm guessing that may be grub needs to be installed to the partition rather than its usual place on the mbr but I'm not sure.

---

