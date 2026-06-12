---
title: "Installation hangs w blank screen/blinking cursors"
date: 2013-06-27
forum: Installation &amp; Upgrades
---

### Post by stefanoradice on 2013-06-27
Hello everybody, new member and 1st post. I cannot install Ubuntu on my new desktop running an Asus Sabertooth z77 mobo and a NVIDIA GTX860 graphic card. No other OS is installed on the machine. **I am experiencing exactly the same problem, occurring at exactly the same step in the installation process, both with 12.04  and 13.04** (desktop, 64 bit)

After choosing Install from the menu, the installation hangs on a blank screen with a blinking cursor. I have tried every suggestion I have found here on this forum, on askubuntu and on the net including

- Disabling Fast Boot and Secure Boot from the BIOS
- Booting with and w/o UEFI
- Enabling nomodeset, nolapic, acpi=off 

No matter what I do, I always get the same result.

Any ideas?

Stefano

---

### Post by stefanoradice on 2013-06-27
I tried disabling quiet splash, the last message displayed is "ata9 hard resetting link"

---

### Post by stefanoradice on 2013-06-29
SOLVED: my DVD was connected to an ASMedia port. Moved it to an Intel SATA port and alla the errors went away

---

