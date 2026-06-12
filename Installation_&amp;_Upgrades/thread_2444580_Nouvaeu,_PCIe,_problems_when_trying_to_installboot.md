---
title: "Nouvaeu, PCIe, problems when trying to install/boot from USB"
date: 2020-06-01
forum: Installation &amp; Upgrades
---

### Post by screek458 on 2020-06-01
Hello All,

I have been having issues trying to install a duel boot of Ubuntu via USB, specifically 20.04. I have also tried installing 18.04 and Mint, as a test. I also verified the checksum of the downloads and they were correct, and also used two different USBs. And yes I have indeed partitioned ssd to prepare for duel booting.  

I will get into the boot menu and boot from the usb, and it will take me to the installation screen for Ubuntu (the purple one) and when I try to either install it or try it, and I will get these errors:

[ATTACH=CONFIG]286061[/ATTACH] 

I have read online that sometimes using nomodeset helps with the nouveau error, however I still have the pcie errors if I do that. What will happen is after about 5 minutes of printing the same error it will go to the ubuntu loading screen and hang there indefinitely until I just hard restart my system. I have also tried using pcie_aspm=off and pci=nommconf in the boot instructions, however this doesn't stop the issues. 

For reference, my computer consists of a Ryzen 3600 with a B450 AsRock Steel Legend motherboard with 32 gb of ram, an Hp EX920 m.2 Nvme drive with 512 gb (this is the drive I plan to boot from), and a Nvidia Geforce 2060 super.  

I pretty much wasted my weekend trying to troubleshoot this on my own and google search solutions to no avail, so any input/ advice would be appreciated. 

Thank you in advance.

---

### Post by ubfan1 on 2020-06-01
First thing to check is that your B450 firmware is the latest. 20.04 should work with the 5.4 kernel.  Check for firmware update on the SSd too.

---

### Post by oldfred on 2020-06-01
In Addition that is a new UEFI system. You should not be getting purple boot screen, but should have black grub menu. And then manually add nomodeset to linux line in grub entry.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See also link below in my signature for more UEFI install info.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

