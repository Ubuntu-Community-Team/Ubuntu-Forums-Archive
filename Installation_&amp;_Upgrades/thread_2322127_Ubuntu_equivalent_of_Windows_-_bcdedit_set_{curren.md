---
title: "Ubuntu equivalent of Windows - bcdedit /set {current} pciexpress forcedisable?"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by Vasco_Reis_Silva on 2016-04-26
So, I have an old PC with an Asrock 4coredual-vsta motherboard, which has both AGP and PCI-Express slots. Currently I have a Radeon 6570 on the PCI-Express slot.

Starting with Windows 8, for it to be properly recognized in Windows, I have to use "bcdedit /set {current} pciexpress forcedisable".

I assume I need something similar for Ubuntu. Right now, the only way I can install and boot into Ubuntu Gnome is if I use "nomodeset". Without "nomodeset", in 16.04 I see the splash, and then just end up with the gnome wallpaper and the mouse cursor, nothing else shows up. In 14.04, I end up with a blank screen.

I already tried pcie_ports=compat/auto/native and acpi_osi=, but they don't solve my issue. Any ideias?

Thank you!

---

### Post by QDR06VV9 on 2016-04-26
> **Vasco_Reis_Silva said:**
> So, I have an old PC with an Asrock 4coredual-vsta motherboard, which has both AGP and PCI-Express slots. Currently I have a Radeon 6570 on the PCI-Express slot.

Starting with Windows 8, for it to be properly recognized in Windows, I have to use "bcdedit /set {current} pciexpress forcedisable".

I assume I need something similar for Ubuntu. Right now, the only way I can install and boot into Ubuntu Gnome is if I use "nomodeset". Without "nomodeset", in 16.04 I see the splash, and then just end up with the gnome wallpaper and the mouse cursor, nothing else shows up. In 14.04, I end up with a blank screen.

I already tried pcie_ports=compat/auto/native and acpi_osi=, but they don't solve my issue. Any ideias?

Thank you!
Hi Vasco_Reis_Silva and Welcome to the forums
I have moved this to Insatll/Upgrades, as this will give you a better chance of help.
Good luck

---

### Post by oldfred on 2016-04-26
I do not know AMD. Radeon 6570

But you are in between old proprietary drivers not being available and updates to the open source AMD drivers having more features.

       [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware). 
With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel
The fglrx driver is now deprecated in 16.04, use radeon and amdgpu 
   AMD driver discussion with 16.04
[http://ubuntuforums.org/showthread.php?t=2321963](http://ubuntuforums.org/showthread.php?t=2321963) 
   How Ubuntu 16.04 Is Performing With AMDGPU/Radeon Graphics Compared To Ubuntu 14.04 With FGLRX
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1)

---

