---
title: "Cant boot"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by theamazinasian22 on 2008-05-31
Recently i did a set of upgrades with the upgrade manager and now when i restarted my computer it couldnt get past the Starting up... screen after the installing grub screen.

---

### Post by Rallg on 2008-05-31
Try re-booting again. Once in a while, for reason I do not understand, that works.

If no luck there: Can you boot to recovery mode? If so, log in, and update and upgrade from there:

sudo apt-get update && sudo apt-get upgrade

Perhaps your first upgrade was "partial," which is often bad news.

---

### Post by theamazinasian22 on 2008-05-31
when i try to boot in recovery mode it stops before finishing the boot

---

### Post by Rallg on 2008-05-31
Sounds like bad news, and in any case that's above my level. Again try to boot to recover mode, and when it hangs, write down the text that is on the screen. That will show which processes succeeded (and thus, which one is causing the hang). Maybe one of the experts can then tell you what to do. Post the screen text here.

---

### Post by theamazinasian22 on 2008-05-31
ok well it stops at

> [11.880998]  ACPI: PCI Interrupt Link[LNKC] enabled at IRQ 1
[11.881049] ACPI:PCI Interrupt 0000:00:03.1[A] -> Link [LNKC] -> GSI 11 (level,low) -> IRQ 11

---

