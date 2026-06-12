---
title: "Small GRUB text after upgrade"
date: 2020-08-09
forum: Installation &amp; Upgrades
---

### Post by ordak on 2020-08-09
Hi,

I upgraded my laptop to Ubuntu 20.04.1 LTS from 18.04 LTS. Many things seem OK but now GRUB text is too small and tough to see. How can I correct it ?

---

### Post by ActionParsnip on 2020-08-09
Do you dual boot? The default is to boot the latest available kernel which is advisable

---

### Post by ordak on 2020-08-10
> **ActionParsnip said:**
> Do you dual boot? The default is to boot the latest available kernel which is advisable

This is a laptop with single Ubuntu LTS OS (no other one) . GRUB version is 2.04 . I removed old kernels but still I get tiny texts in GRUB.

---

### Post by oldfred on 2020-08-10
Do you have a 4K screen?
There are both gfxsettings for screen size & font settings in grub.
But grub tries to use screen settings from installed system.

[https://www.gnu.org/software/grub/manual/grub/html_node/Theme-file-format.html#Theme-file-format](https://www.gnu.org/software/grub/manual/grub/html_node/Theme-file-format.html#Theme-file-format)
[https://www.gnu.org/software/grub/manual/grub/html_node/loadfont.html#loadfont](https://www.gnu.org/software/grub/manual/grub/html_node/loadfont.html#loadfont)

Details on your own font:
[https://unix.stackexchange.com/questions/31672/can-grub-font-size-be-customised](https://unix.stackexchange.com/questions/31672/can-grub-font-size-be-customised)

---

### Post by ordak on 2020-08-11
> **oldfred said:**
> Do you have a 4K screen?


[...]

According to Setting>Displays current resolution is 1368 x 768 . Max resolution is 1920 x 1080 .

---

