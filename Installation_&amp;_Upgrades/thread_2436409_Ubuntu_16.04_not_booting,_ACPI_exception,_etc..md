---
title: "Ubuntu 16.04 not booting, ACPI exception, etc."
date: 2020-02-05
forum: Installation &amp; Upgrades
---

### Post by yzhou377 on 2020-02-05
[COLOR=#141414][FONT=&quot]Hi I am using a ubuntu 16.04 on Alienware Aurora R8, the OS is installed in a Dell 512G SSD, and I also have a data-drive which is 1 Samsung 4T SSD.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Everything works perfectly until this afternoon. The system fails to boot.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]I have attached the screen-shot of the failure message here.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Any help would be appreciated.

[/FONT][/COLOR][ATTACH=CONFIG]284976[/ATTACH]

---

### Post by oldfred on 2020-02-05
That is a new system and needs the latest kernel, drivers & support software. or even the not yet released 
Better to use 18.04LTS, but you may even need.
 
Have you updated UEFI & SSD firmware?
Better to make sure UEFI Secure Boot is off, and UEFI fast start up is off.
Change drives to AHCI. If dual booting with Windows install Windows AHCI driver first.
Since you have nVidia you need nomodeset boot parameter for both live install and until  you install the nVidia driver into your install.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Alienware will be similar to similarly configured Dell systems.
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)

---

