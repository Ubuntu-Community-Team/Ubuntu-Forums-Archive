---
title: "GRUB won't load Ubuntu 8.10"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by beermattuk on 2008-11-06
I recently installed ubuntu (kubuntu) 8.10 and GRUB won't load, I get a "disk boot failure, insert system disk" error.  It doesn't even get as far as the GRUB loader or menu.

I have a PCI IDE card with 2 x IDE HDDs connected, the first of which I've just installed Kubuntu on.  I've also got an onboard 250GB SATA with windows XP on it.

The boot order in the bios is set to boot to the IDE card first, the IDE card boots to the correct disk, and fdisk -l shows a * next to the kubuntu partition.  Yet it still won't boot.

If I DISABLE the SATA controller altogether on my mainboard then it will boot - !??  But as soon as I re-enable it (again checking boot order/priority is correct) it stops working again.

Any ideas?  Thanks.

---

