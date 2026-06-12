---
title: "deleted Ubuntu, can't boot Windows"
date: 2015-02-10
forum: Installation &amp; Upgrades
---

### Post by Askel on 2015-02-10
I deleted ubuntu on my Surface pro with Win 8.1. I deleted the partitions, rebooted it and with the commandprompt wrote bootrec.exe /fixmbr as I read in numerous guides. I also tried the automatic repair. But it just won't work. I just get to GNU GRUB minimal. What did I do wrong, and how do I fix it?

edit:
I also tried this [B]bootsect /nt60 SYS /mbr

[/B]it said "Successfully updated FA32 filesystem bootcode" under HardiskVolume2
Under Hardisk0/DR0 it said:
"bootcode is only updated on MBR partitioned disks. A different partitioning scheme is used on this disk. Bootcode was successfully updated on all targeted volumes"

---

### Post by oldfred on 2015-02-10
Your system is UEFI, not MBR unless you modified it yourself.

And if UEFI, you should just go back into UEFI boot menu can choose to boot Windows. You also may have a one time boot key.

Or did you also delete Windows? With UEFI it has many partitions.

---

