---
title: "asus EEEPC 1005ha ubuntu install problem"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by accesslifecomputer on 2012-03-04
hello, i have asus eeepc 1005ha 160 gb sata  and 1gb ram.
please help me with this problem.
i was able to install ubuntu 11 and install was completed, however after rebooting it says "error read file". i forced shut off my eeepc then start it again, i tried the recovery mode this time and this is what it says


[    0.952556] md: Waiting for all devices to be available before aurodetect
[    0.952646] md: If you don't use raid, use raid=noautodetect
[    0.953213] md: Autodetecting RAID arrays
[    0.953300] md: Scanned 0 and added 0 devices.
[    0.953375] md: autorun...
[    0.953444] md: ...autorun DONE.
[    0.953705] VFS: Cannot open root device "UUID=cc8ca1f4-e668-45ed-9c11-5debc485ea95" or unknown-block (0,0)
[    0.953825] Please append a correct "root=" boot option; here are the available partitions:
[    0.953953] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
[    0.954065] Pid: 1, comm: swapper Not tainted 3.0.0-12-generic #20-Ubuntu
[    0.954152] Call trace:
[    0.954238] [<c1518c98>] ? printk+0x2d/0x2f
[    0.954317] [<c1518b76>] panic+0x5c/0x151
[    0.954403] [<c17bcb2b>] mount_block_root+0xb9/0x114c
[    0.954485] [<c1135f7c>] ? sys_mknod+0x2c/0x30
[    0.954571] [<c17bcd36>] mount_root+0x59/0x5f
[    0.954648] [<c17bce8a>] prepare_namespace+0cx14e/0x192
[    0.954736] [<c1127235>] ? sys_access+0x25/0x30
[    0.954821] [<c17bc89f>] kernel_init+0x136/0x13b
[    0.954900] [<c17bc769>] ? start_kernel+0x358/0x358
[    0.954986] [<c1533b7e>] kernel_thread_helper+0x6/0x10

this is what it shows and it doesnt move on.... thank you for your help

---

