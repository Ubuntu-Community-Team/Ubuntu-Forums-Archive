---
title: "Unable to install Ubuntu on Thinkpad E425, freezes on splash screen"
date: 2018-12-17
forum: Installation &amp; Upgrades
---

### Post by waninstall on 2018-12-17
Every time I try booting off USB and selecting install Ubuntu or try Ubuntu, it flashes a "do_irq 1.55 no irq handler for vector" error and then freezes on the splash screen after about 10 seconds. 

If I add option acpi=off, I get a bunch of "nobody cares" errors. "disabling irq#17, irq 18: nobody cared(try booting with the "irqpoll" option), then about 8 lines of usb2-3 and usb3-4 device not accepting address 2, error -110. Then, two lines of usb usb2-port3: unable to enumerate usb device. Then goes to the splash screen fails after about 30 seconds with:

(initramfs) unable to find a medium containing a live file system. 

I've tried updating the bios, toggling all the boot options, tried multiple usb devices. Same problem. At this point I've been trying to get passed the splash screen for 6 hours.

Edit: booting with nomodeset and noapic has allowed me to get into the installation screen. However I do get the error: "[drm:radeon_init [radeon]] *ERROR* No UMS support in..."

---

