---
title: "&quot;failed to get unique processor _uid&quot; error trying to boot focal insaller"
date: 2021-01-09
forum: Installation &amp; Upgrades
---

### Post by c@ssie on 2021-01-09
I have a ga-x79-ud5 motherboard in a PC  with no installed OS.  I  can't boot from USB, and when I enter the BIOS setup I only can get to a  screen that doesn't have any relevant settings.

On my mac I put  on a HDD in a SATA to USB dock. and used the commmand:[COLOR=#800000] ```
[FONT=lucida console]sudo dd if=ubuntu-mate-20.04.1-desktop-amd64.iso of=/dev/rdisk2 bs=1m [/FONT]
```[/COLOR](that's the mac equivalent of[COLOR=#800000]sudo dd if=ubuntu-mate-20.04.1-desktop-amd64.iso of=/dev/sdc bs=1M[/COLOR]).

When I put it in the PC, and tried to boot from it I got the following: 
```
[COLOR=#800000]acpi lnxcpu:01: Failed to get unique processor _uid (0x0)
[COLOR=#800000]acpi lnxcpu:02: Failed to get unique processor _uid (0x0[/COLOR]
[COLOR=#800000]acpi lnxcpu:03: Failed to get unique processor _uid (0x0
[/COLOR].....
acpi lnxcpu:1d: Failed to get unique processor _uid (0x0)
initramfs unpacking failed: decoding failed[/COLOR][COLOR=#ff0000]
[/COLOR]
```

---

