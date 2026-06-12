---
title: "PCI error during LIVECD start"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by witmann on 2007-09-19
Hello,

I have a problem with launching (and, as a consequence, installing) Ubuntu 6.06 from LiveCD.
I've searched a lot for an answer of my question, but couldn't get a satisfing one.
I had two errors:

[42944668.895000].. MPBIOS bug: 8254 timer not connected to IO-APIC

AND

[42944668.028000] PCI: cannot allocate resource region 3 of device 0000:00:00.0

However, the first one was fixed with the "noapic"  boot command, but the second one is still a mistery.

The problematic PC is a Fujitsu Siemens Esprimo Edition P2510, running on Celeron D 3,33Ghz.

I would be really grateful if someone could help me with this issue.

---

### Post by Pumalite on 2007-09-19
Try:

"acpi=off"  "noacpi"

---

### Post by witmann on 2007-09-19
i tried all commands given in a big HOW-TO by **tseliot**, but with no results.

---

### Post by Pumalite on 2007-09-19
I'll give you a few more to choose from:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html)

---

