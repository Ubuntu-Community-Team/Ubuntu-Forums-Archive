---
title: "Dual Boot Install Stops With IRQ Errors"
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by kincanonmi on 2014-10-13
I have tried the install of Ubuntu and Mint to dual boot on my HP 360. I've followed the pre-setup and boot with Ubuntu on a USB stick. The process starts just fine and then ends with an IRQ error.

I have a HP Privilion 360 with an Intel N3530 @ 2.16 GHZ CPU 64 bit with 8 Gig of RAM. I've gone through the process of freeing space on the HD and disabling FastBoot and IEF boot. I created a USB stick with Unbootin with both Ubuntu 14.04 and Mint 17 - 64 bit. All goes well until I tell the installation to load in try-first mode. When the boot begins it runs OK and then stops with the final lines as follow:

Stop mount in file system on boot

[23.8091301] 12_c designware 80860F41:00: failure requesting IRQ 32

[23.814954] 12_c designware 80860F41:01: failure requesting IRQ 33

[48:155045] bug: soft lockup-CPU#3 stuck for 2251 [systemd-udevd:1039]

I'd really appreciate any help as to why this occurs and how to fix the problem so I get a real OS installed that I uses 98% of the time.

Mike

---

### Post by oldfred on 2014-10-14
I had no idea what a 12_c designware is.

But it seems to be a touchpad that needs an added driver.
[http://ubuntuforums.org/archive/index.php/t-2190187.html](http://ubuntuforums.org/archive/index.php/t-2190187.html)

Not sure how you get past the IRQ errors, but I might try one of these boot options. Add like you would a nomodeset option.

       BIOS live installer Boot Options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)


 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

