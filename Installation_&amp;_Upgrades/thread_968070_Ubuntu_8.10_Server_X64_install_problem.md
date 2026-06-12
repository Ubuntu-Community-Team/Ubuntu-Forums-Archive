---
title: "Ubuntu 8.10 Server X64 install problem"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by kuijern on 2008-11-02
I'm trying to install Ubuntu 8.10 Server X64, the cd boots but when i say install i get the following message:

[B][    1.865604]  [<ffffffff80209000>] ? _stext+0x0/0x1000
[    1.865652]  [<ffffffff80235727>] change_page_attr_set_clr+0xa7/0x200
[    1.865703]  [<ffffffff80225000>] ? init_intel_pdc+0xb0/0x150
[    1.865752]  [<ffffffff802b3460>] ? free_hot_page+0x10/0x20
[    1.865801]  [<ffffffff802b3e15>] ? __free_pages+0x35/0x40
[    1.865849]  [<ffffffff80209000>] ? _stext+0x0/0x1000
[    1.865896]  [<ffffffff802358d8>] set_memory_ro+0x18/0x20
[    1.865944]  [<ffffffff80232eaa>] mark_rodata_ro+0x7a/0xa0
[    1.865992]  [<ffffffff8020a1e8>] init_post+0x18/0x1b0
[    1.866043]  [<ffffffff8072083b>] kernel_init+0x112/0x128
[    1.866093]  [<ffffffff802444d7>] ? schedule_tail+0x27/0x70
[    1.866140]  [<ffffffff80212c99>] child_rip+0xa/0x11
[    1.866188]  [<ffffffff80720729>] ? kernel_init+0x0/0x128
[    1.866235]  [<ffffffff80213c8f>] ? child_rip+0x0/0x11
[    1.866280]
[    1.866318]
[    1.866355] Code: ff 6a d4 e9 1c bf ff ff 6a d3 e9 15 bf ff ff 6a d2 e9 0e bf
 ff ff 6a d1 e9 07 bf ff ff 6a d0 e9 00 bf ff ff 6a cf e9 f9 be ff ff <6a> ce e9
 f2 be ff ff 6a cd e9 eb be ff ff 6a cc e9 e4 be ff ff
[    1.866566] RIP  [<ffffffff80216f97>] IRQ0x31_interrupt+0x0/0x7
[    1.866566]  RSP <ffff88007e009cc8>
[    1.866566] CR2: 0000000000648000
[    1.866566] ---[ end trace d5df64b80c0f703c ]---
[    1.868222] Kernel panic - not syncing: Attempted to kill init![/B]

Sysinfo:
Intel D945GCLF2 (DC Atom 330)
Kingston KVR533D2N4/2G 2GB 533MHz DDR2
Kingston 4GB CompactFlash Card (connected by a ide to compactflash adapter)
2x WD 1TB 7200rpm 16mb Sata
Liteon 16x DVD+R/W (connected by a ide to usb adapter)

I've tried a number of hardware combinations also removing the drives and directly connecting the DVD+R/W.

I've also tried the latest bios version, but nothing works.

---

### Post by Wurlitzer on 2008-12-07
I had the exact same problem, solved it by updating the bios to version 0122 and loading Optimum defaults.

//W

---

