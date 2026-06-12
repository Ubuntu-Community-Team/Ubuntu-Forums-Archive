---
title: "grub/boot help"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by afbase on 2006-07-21
is there a way to modify my grub boot file through nano or vi editor?
i would like to insert 'ACPI=off' it without restarting my server.
i typed 'dmesg' in my command prompt and it returned numerous:
 ACPI-0674: *** Error: acpi_ev_gpe_dispatch: No handler or                                               method for GPE[34], disabling event

---

### Post by 5-HT on 2006-07-21
The config file is /boot/grub/menu.lst and can be edited with any text editor. You can append 'acpi=off noacpi' to the relevant kernel line. Note that changes will not take effect until the next boot.

HTH

---

### Post by afbase on 2006-07-21
Thanks!!!!

I haven't really modified it that way before.  it helped that you mentioned to put it on the relevant kernel line, or i might have been lost.

---

