---
title: "Ubuntu not starting"
date: 2015-04-03
forum: Installation &amp; Upgrades
---

### Post by matthias14 on 2015-04-03
Hello!

When I try to install Ubuntu next to my Windows 8, neither the bootloader (grub I suppose) show up, nor does a new entry in the uefi boot menu appear. I tried installing Ubuntu both with the EFI system partition (/dev/sda1) mounted as /boot/efi and without (both were given as contradictory hints in the UEFI guide). Secure boot is turned off.

[http://paste.ubuntu.com/10706109](http://paste.ubuntu.com/10706109)

The paste shows the stadium when I tried to make the root partition (/dev/sda9) encrypted, but I have also tried it without since then.

Regards,
Matthias

---

### Post by mateojonsonguynn on 2015-04-03
This probably will not work, but just a suggestion:
Maybe try holding down or repeatedly pressing the shift button while your computer is turning on (right after you press the power button). Continue holding it down/pressing until either grub appears (yay) or the Windows 8 logo appears (Sorry. This was my only suggestion).

---

### Post by matthias14 on 2015-04-04
Thanks for the suggestion, but unfortunately neither holding shift nor repeatedly pressing it brought up a grub menu, just the usual Windows 8.

---

