---
title: "Abort, the amd64 build has not succeeded"
date: 2022-10-21
forum: Installation &amp; Upgrades
---

### Post by pelomorao on 2022-10-21
Hello,

I have a problem updating the Kernel of my ubuntu 20.04, I have version 5.4.0-131-generic and to update the Kernel I have used the script ubuntu-mainline-kernel.sh but when I run it it finds the latest version of Kernel (v6 .0.2) but when starting the installation I get the following error:


```
[COLOR=#000000][FONT=Menlo]./ubuntu-mainline-kernel.sh -i
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]Finding latest version available on kernel.ubuntu.com[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Latest version is: v6.0.2, continue? (y/N) y[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Abort, the amd64 build has not succeeded[/FONT][/COLOR]

```

Do you know how I can solve it?


PS: I want to update the Kernel because at boot I have these errors and after trying to update the BIOS and continue with the same errors, I would like to try updating the Kernel:


```
Oct 20 03:43:59 LexPlay2 kernel: [   68.527447] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   68.621456] ipmi_si IPI0001:00: IPMI message handler: Found new BMC (man_id: 0x00c1d6, prod_id: 0x0707, dev_id: 0x20)
Oct 20 03:43:59 LexPlay2 kernel: [   68.627867] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   68.767371] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   68.767372] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   68.767379] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   68.861479] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   68.987348] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   68.987349] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   68.987355] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   69.080162] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   69.171867] ipmi_si IPI0001:00: IPMI kcs interface initialized
Oct 20 03:43:59 LexPlay2 kernel: [   69.195348] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   69.195348] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   69.195351] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   69.295672] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   69.363336] ipmi_ssif: IPMI SSIF Interface driver
Oct 20 03:43:59 LexPlay2 kernel: [   69.411317] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   69.411319] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   69.411322] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   69.514646] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   69.642827] Adding 524284k swap on /dev/nvme1n1p3.  Priority:-2 extents:1 across:524284k SSFS
Oct 20 03:43:59 LexPlay2 kernel: [   69.655471] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   69.655472] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   69.655474] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   69.750000] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   69.878831] Adding 524284k swap on /dev/nvme0n1p3.  Priority:-3 extents:1 across:524284k SSFS
Oct 20 03:43:59 LexPlay2 kernel: [   69.879184] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   69.879185] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   69.879187] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   69.969263] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   70.115609] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   70.115610] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   70.115615] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   70.205465] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   70.359627] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   70.359628] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   70.359633] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   70.454567] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   70.591106] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   70.591106] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   70.591109] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   70.677228] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   70.795417] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   70.795418] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   70.795420] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   70.895513] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   71.011530] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   71.011531] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   71.011533] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   71.098567] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   71.223604] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   71.223605] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   71.223610] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   71.315850] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   71.443319] EDAC amd64: Node 0: DRAM ECC enabled.
Oct 20 03:43:59 LexPlay2 kernel: [   71.443320] EDAC amd64: F19h detected (node 0).
Oct 20 03:43:59 LexPlay2 kernel: [   71.443322] EDAC amd64: Error: F0 not found, device 0x1650 (broken BIOS?)
Oct 20 03:43:59 LexPlay2 kernel: [   71.527614] EDAC amd64: Error: Error probing instance: 0
Oct 20 03:43:59 LexPlay2 kernel: [   71.631244] EDAC amd64: Node 0: DRAM ECC enabled.
```

---

### Post by pelomorao on 2022-10-21
I have already solved it by installing Kernel 5.10 by hand

---

### Post by Impavidus on 2022-10-21
Kernel 5.15 is available for 20.04 from the repositories:```
sudo apt install linux-generic-hwe-20.04
```
That will install the metapackage that will pull in the latest 5.15 kernel, with automatic updates.

---

### Post by pelomorao on 2022-10-21
> **Impavidus said:**
> Kernel 5.15 is available for 20.04 from the repositories:```
sudo apt install linux-generic-hwe-20.04
```
That will install the metapackage that will pull in the latest 5.15 kernel, with automatic updates.


Thank you very much!! :D

---

