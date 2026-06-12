---
title: "kernel crash ?"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by kuleali on 2005-03-20
i am usig the 2.6.10-5-386 kernel and my system freezes after some min. , am i the only one with this kind of ptoblem?

is there any solution.

---

### Post by mmealman on 2005-03-20
Have you tried adding acpi=off to your boot options?

title           Ubuntu, kernel 2.6.10-5-k7
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.10-5-k7 root=/dev/hda2 ro **acpi=off** quiet splash
initrd          /boot/initrd.img-2.6.10-5-k7
savedefault
boot

---

### Post by gnutux on 2005-03-20
ACPI should only be turned off if your system doesn't support ACPI v2.0. Else, your system would use APM instead.

gnutux

---

