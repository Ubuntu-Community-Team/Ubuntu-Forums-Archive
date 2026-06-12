---
title: "TBT disk boot failure after 24.04 upgrade to 6.8.0-38"
date: 2024-07-15
forum: Installation &amp; Upgrades
---

### Post by universalkludge on 2024-07-15
Hi,

External TBT disk boot failure after 24.04 upgrade to linux-modules-6.8.0-38-generic - boots into initramfs; works fine w/ linux-modules-6.8.0-36-generic
What is noticed that in the failure case this line is missing in the dmesg:

ACPI: bus type thunderbolt registered


grep against nvme

boot failure 

[    1.789495] nvme nvme0: pci function 0000:02:00.0
[    1.789497] nvme nvme1: pci function 0000:05:00.0
[    1.789514] nvme 0000:02:00.0: enabling device (0000 -> 0002)
[    1.793255] nvme nvme0: Shutdown timeout set to 10 seconds
[    1.807844] nvme nvme0: allocated 64 MiB host memory buffer.
[    1.833440] nvme nvme0: 12/0/0 default/read/poll queues


boot ok

[    1.754624] nvme nvme0: pci function 0000:02:00.0
[    1.754630] nvme 0000:02:00.0: enabling device (0000 -> 0002)
[    1.754631] nvme nvme1: pci function 0000:05:00.0
[    1.758230] nvme nvme0: Shutdown timeout set to 10 seconds
[    1.772859] nvme nvme0: allocated 64 MiB host memory buffer.
[    1.798671] nvme nvme0: 12/0/0 default/read/poll queues
[    1.831580] nvme nvme1: 12/0/0 default/read/poll queues
[    1.838160] nvme nvme1: Ignoring bogus Namespace Identifiers
[    1.844266]  nvme1n1: p1 p2
[    3.920118] EXT4-fs (nvme1n1p2): mounted filesystem 29ed8d33-f0b5-4cc2-bf4d-c49eda875721 ro with ordered data mode. Quota mode: none.
[    4.153671] systemd[1]: Starting [email]modprobe@nvme_fabrics.servic[/email]e - Load Kernel Module nvme_fabrics...
[    4.165931] systemd[1]: [email]modprobe@nvme_fabrics.servic[/email]e: Deactivated successfully.
[    4.166149] systemd[1]: Finished [email]modprobe@nvme_fabrics.servic[/email]e - Load Kernel Module nvme_fabrics.
[    4.181564] EXT4-fs (nvme1n1p2): re-mounted 29ed8d33-f0b5-4cc2-bf4d-c49eda875721 r/w. Quota mode: none.

Any help would be appreciated.

Thanks
Andrew

---

### Post by romste on 2024-08-31
Hi Andrew,

I have the same problem, still with kernel 6.8.0-41.
With kernel 6.8.0-36 it works, with every new kernel so far it does not.


Have you (or someone else) found a solution in the meantime?

Regards,
Roman

---

### Post by romste on 2024-09-01
Hi Andrew,

See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2078573](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2078573)

*[COLOR=#000000][FONT=&quot]Try adding thunderbolt.[/FONT][/COLOR][COLOR=#000000][FONT=&quot]host_reset=[/FONT][/COLOR]*[COLOR=#000000][FONT=&quot]*0 to your kernel command line.*


[/FONT][/COLOR]This works for me.

Regards,
Roman

---

