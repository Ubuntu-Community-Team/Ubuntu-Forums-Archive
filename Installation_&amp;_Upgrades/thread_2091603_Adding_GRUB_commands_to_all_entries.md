---
title: "Adding GRUB commands to all entries"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by trogdor1138 on 2012-12-05
How can I add GRUB commands to all Linux entries without manually editing /boot/grub/grub.cfg?

I'm not referring to kernel parameters, but actual commands that get executed before booting the kernel. Basically, I need code to execute after selecting a menu entry, but before booting the actual kernel.

I'm running 12.10 on my MacBook Pro 8,2 in EFI mode. The GRUB EFI application is installed on the hard drive's ESP, with the /boot directory being on the Ubuntu partition.

These MBP's have dual GPU's; an integrated Intel controller and a discrete AMD one. For battery saving and heat management, I'm currently completely disabling the Radeon GPU and using only the Intel one. This is done by adjusting the gmux controller's registers like so:

outb 0x728 1 
outb 0x710 2 
outb 0x740 2 
outb 0x750 0

I've edited the following:

/etc/defaults/grub - Disabled the OS prober and added i915 kernel parameters required to boot
/boot/grub/custom.cfg - Contains only the above 'outb' commands

This works, and allows me to use 'update-grub', but the caveat is that the outb code gets executed before loading the GRUB menu. This renders the display unusable until the kernel boots, meaning I can't see the GRUB menu. The laptop boots fine, but there's no reliable way to select other entries or edit kernel parameters.

So again, how can I add code to each linux entry to be executed just before launching the kernel, without editing grub.cfg manually?

---

