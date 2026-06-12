---
title: "Ubuntu 8.04:After update to kernel 2.6.24-26 QEMU/KVM doesn't boot Windows XP anymore"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by zipjebt on 2009-12-06
I'm using a virtual Windows XP machine under QEMU/KVM for some time to run programs which are available under Windows only. Up to kernel 2.6.24-24 everything was working fine. Starting from kernel 2.6.24-25 the virtual Windos XP machine doesn't boot anymore. The window just remains black and KVM hangs. 

I'm using the following command

kvm -hda disk.img -cdrom winXP.iso -m 512 -net nic -net user -localtime -no-reboot

Other operating system like MS-DOS or systemRescueCD are still working.

Does somebody experience a similiar problem and maybe does know what causes the problem?

---

### Post by abdougal on 2010-02-23
Same here... downgraded back 2.6.24-24 and it works fine. Still is broken with 2.6.24-27. Regular qemu works fine.

---

