---
title: "Ubuntu Studio 64'install fails"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by Tabou on 2009-12-18
Hello,

I tried several times to install " Ubuntu Studio 64 " on a disk Seagate 250 Gb, then on 3 other disks, but at the reboot, the computer freezes :

[IMG]http://www.casimages.com/img.php?i=091218092701929345083673.jpg[/IMG]

> [    0.366999] Call Trace:
[    0.366999]  [<ffffffff802787a1>] tick_handle_periodic+0x21/0x90
[    0.366999]  [<ffffffff8022f6f2>] hpet_interrupt_handler+0x12/0x30
[    0.366999]  [<ffffffff802a44fd>] handle_IRQ_event+0x6d/0x150
[    0.366999]  [<ffffffff802050c8>] thread_edge_irq+0x88/0x100
[    0.366999]  [<ffffffff802a535a>] do_irqd+0xca/0x170
[    0.366999]  [<ffffffff802a5290>] ? do_irqd+0x0/0x170
[    0.366999]  [<ffffffff8026c879>] kthread+0x49/0x90
[    0.366999]  [<ffffffff80214b49>] child_rip+0xa/0x11
[    0.366999]  [<ffffffff8026c830>] ? kthread+0x0/0x90
[    0.366999]  [<ffffffff80214b3f>] ? child_rip+0x0/0x11
[    0.366999] Code: 2e 0f 1f 84 00 00 00 00 00 39 3d a2 fb 75 00 55 48 89
 2c 65 48 8b 14 25 08 00 00 00 48 c7 c0 90 95 a8 80 31 ff 48 8b 04 10 <f6>
 00 00 00 03 40 0f 95 c7 e8 ee 73 fe ff c9 c3 0f 1f 40
[    0.366999] RIP  [<ffffffff80278722>] tick_periodic+0x22/0x80
[    0.366999]  RSP <ffff88012e803e00>
[    0.366999] CR2: 0000000000000088
[    0.366999] ---[ end trace 4eaa2a86a8e2d22 ]---[IMG]http://www.casimages.com/img.php?i=091218092701929345083673.jpg[/IMG]

Thank you for your answer


Motherboard : Asus M4A77TD
Processor : AMD Athlon(tm) II X2 245
Graphic Card : Asus EN9500 GT (GeForce)
Memory : Kingston 4 Gb

---

