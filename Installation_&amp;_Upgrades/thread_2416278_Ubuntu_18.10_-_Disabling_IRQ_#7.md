---
title: "Ubuntu 18.10 - Disabling IRQ #7"
date: 2019-04-08
forum: Installation &amp; Upgrades
---

### Post by liaquore on 2019-04-08
When I try to run Linux Ubuntu without installing, I get this as the output:

[    5.637375] irq 7: nobody cared (try booting with the "irqpoll" option)
[    5.637545] handlers:
[    5.637558] [<0000000035311cc6>] amd_gpio_irq_handler
[    5.637581] Disabling IRQ #7

And it freezes on that. PC specs:

CPU: AMD Ryzen 5 1500X
GPU: Gigabyte RX 550 2GB
Motherboard: Gigabyte AB350M-D3H
RAM: 8GB DDR4 @ 2134Mhz
Storage 1: M.2 256GB SSD (disconnected because I suspect it is broken)
Storage 2: 1TB HDD

My computer has previously had Windows 10 Professional installed on it, but it stopped working (most likely due to my SSD). My computer freezes when trying to load the Windows installer, but running Ubuntu without installing works perfectly, so I'm trying to install it onto my hard drive. That output is what I get when running without installing, and apparently using the "irqpoll" thing is a bad permanent fix. Plus, when I try to install Linux, it stays on a black screen.

Any ideas on how to debug this?

---

### Post by liaquore on 2019-04-12
bump

---

