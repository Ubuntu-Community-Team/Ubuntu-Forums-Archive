---
title: "Troubleshoot dual-boot Windows 10 - Ubuntu 20.04 LTS on Asus G15"
date: 2021-07-15
forum: Installation &amp; Upgrades
---

### Post by Anh_Tran on 2021-07-15
Dear all,

I'm a frequent user of Ubuntu since 14.04. I have a hard time installing Ubuntu 20.04 on my new laptop. I have done the following.

* Disable Fast Boot in BIOS
* Disable Secure Boot in BIOS
* Make sure SATA connection is selected with the PCIe NVMe SSD
* Install Ubuntu 20.04 LTS on a USB drive via Rufus

A few specs about my laptop:
* Asus G15
* AMD R7-5800H
* NVIDIA GeForce RTX 3050 Ti
* SSD

In the Grub menu, press 'e' and put in ```
nouveau.modeset=0
``` as described in [https://liamfrappell.medium.com/fixing-black-screen-and-keyboard-shutdown-issues-on-an-asus-rog-strix-scar-2021-laptop-in-ubuntu-20-9ce964bf34d0](https://liamfrappell.medium.com/fixing-black-screen-and-keyboard-shutdown-issues-on-an-asus-rog-strix-scar-2021-laptop-in-ubuntu-20-9ce964bf34d0) (if this is not done, then the resolution is 800x600 and I will have a harder time navigating with the unseen bottom of the install windows). All in all, it says I finished the installation. My problem is that it can't boot from the installed Ubuntu, it would just give me a black screen and do not advance from there. I have tried various ways, but I don't seem like I can break through here. Please let me know if there is anything else I can do to make this dual boot.

Many thanks.

---

### Post by oldfred on 2021-07-15
Newest versions of Ubuntu now offer to install proprietary driver during install.
If not installed during install, you need the nomodeset boot parameter for first boot or until you install proprietary driver.

If not dual booting, you need to press escape right after UEFI screen, but before grub menu normally appears. May have to try several times as timing is critical. Then you get grub menu and can add nomodeset into boot stanza or boot recovery mode.
Safe Graphics Boot option on installer adds nomodeset.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

