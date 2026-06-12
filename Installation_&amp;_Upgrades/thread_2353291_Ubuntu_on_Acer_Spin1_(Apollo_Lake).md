---
title: "Ubuntu on Acer Spin1 (Apollo Lake)"
date: 2017-02-20
forum: Installation &amp; Upgrades
---

### Post by ppetterr on 2017-02-20
Hello,
I have tried boot Ubuntu 16.10/17.04 on my Acer Spin1 (CPU: Apollo Lake Intel Celeron N3450/GPU: Intel HD Graphics 500/BIOS: InsydeH20 Setup Utility Rev. 5.0, Version: 1.01/RAM: 4GB/HDD: eMMC 32GB) but I had no luck with it. Originally there was Windows 10 installed but I formatted HDD with the Arch linux (the only one linux distribution which I could boot properly). What have I tried:
- disabled Secure Boot option in BIOS
- added an UEFI file as trusted for executing from the USB with installed Ubuntu in BIOS
- created bootable USB with rufus or directly from a computer with Ubuntu installed
The problem is when I try to boot the Ubuntu from USB I only see white underscore character in the upper-left corner of the screen and Acer logo in the middle of the screen. Do you have some idea about this situation? Is it something wrong with grub or do I need to wait for new kernel 4.10 in Ubuntu 17.04? Personally, I have no idea how I can boot Ubuntu on the Acer Spin1 properly and also in this situation I have no logs which I can provided for you (sorry for my English). Thank you.

---

### Post by oldfred on 2017-02-21
You may need nomodeset?

Are you booting in BIOS or UEFI boot mode?
Have you installed latest UEFI from Acer?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Other Acer models. Once installed, Acer has a unique requirement of setting an UEFI supervisory password and then from inside UEFI drill down to /EFI/ubuntu and set trust on the .efi boot files.


 Acer Aspire ES1-132 cannot able to install kubuntu UEFI missing options, rEFInd
[https://ubuntuforums.org/showthread.php?t=2348269](https://ubuntuforums.org/showthread.php?t=2348269)
Acer Aspire R5-417T
[https://ubuntuforums.org/showthread.php?t=2346815](https://ubuntuforums.org/showthread.php?t=2346815)
Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by ppetterr on 2017-02-22
Thank you Sir. I did a lot of testing and it seems that BIOS v1.01 for Spin SP111-31 is buggy. I asked Acer technical support if they check the situation or provide me a newer version of BIOS. So, we will see...I will share my experiences with you.

---

### Post by ppetterr on 2017-03-02
So the solution is enabling "Network Boot" and "F12 Boot Menu" in BIOS.

---

### Post by m666 on 2017-04-01
> **ppetterr said:**
> So the solution is enabling "Network Boot" and "F12 Boot Menu" in BIOS.

So is ubuntu working fine on Spin1?

---

