---
title: "Ubuntu 14.04 64Bit AMD - Rebooting during bootup after fresh install"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by cynergy on 2014-04-24
Hi All,

Experiencing a weird fault.... I'm using an Samsung NP355V5C-901AU notebook... AMD CPU, 8GB RAM, ATI Radeon Graphics, 500GB AHCI HDD. 

The live USB boots up just fine and allows me to install Ubuntu to the notebook, no problems. After the reboot, the kernel reboots a few seconds into the loading, somewhere around checking for DSDT tables. Have tried enabling / disabling various bios options - same fault continues. I'm currently going through the boot time messages from the live usb to try to find why it loads but the installed copy doesn't.

If anyone could shed light on this issue I'd be most grateful...

Cheers,

Cynergy.

---

### Post by cynergy on 2014-04-24
More to note: If I add acpi=off during the boot, the kernel panics with this error: Boot APIC ID in local APIC unexpected (0 vs 16)

the line before it states: weird, boot CPU (#0) not listedby the bios.

---

