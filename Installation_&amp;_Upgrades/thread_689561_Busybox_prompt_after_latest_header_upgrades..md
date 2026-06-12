---
title: "Busybox prompt after latest header upgrades."
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by PinkFloyd102489 on 2008-02-06
One of our Core 2 Duo's in Computer Engineering is crashing to a BusyBox prompt on boot. It's the only one that's been upgraded to the latest kernel headers, so I suspect that is the culprit.

Any way to fix?

---

### Post by taurus on 2008-02-06
Is there an error message on the screen before it drops into that prompt?

---

### Post by PinkFloyd102489 on 2008-02-06
Nope, no error. Just drops to BusyBox.

---

### Post by taurus on 2008-02-06
Can you access your filesystem where / is?

```
df -h
```
If you can, edit /boot/grub/menu.lst and remove the **quiet** (before **splash**) from the entry for kernel so you would know what process causes to bail out.

---

### Post by Heinzelotto on 2008-02-06
the error is probably caused by a missing ACPI; i sometimes get this error when trying to start linux-live-cds in qemu (which afaik doesn't support ACPI). Try booting with the kernel-parameter 'acpi=off'

---

