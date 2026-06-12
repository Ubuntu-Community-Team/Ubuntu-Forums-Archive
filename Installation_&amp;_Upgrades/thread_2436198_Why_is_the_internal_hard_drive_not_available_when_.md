---
title: "Why is the internal hard drive not available when attempting to install Ubuntu 18.04"
date: 2020-02-02
forum: Installation &amp; Upgrades
---

### Post by linuxguiri on 2020-02-02
When I attempt to install either Ubuntu 18.04 or 19.10 from a USB flash drive to a Dell Latitude 5500 PC, only the USB drive appears on the "Allocate Drive Space" screen (as sda); the internal hard drive (SSD) is not visible. In other words, I can only install Ubuntu to the USB flash drive; the hard drive is not an option. How can I make the hard drive visible so that I can install to it?

---

### Post by CelticWarrior on 2020-02-02
You need to change the SATA mode from whether it is, usually RAID, to AHCI. But be aware that if you want to have a dual-boot with Windows you need to install AHCI support before making the change or Windows won't boot.

---

### Post by oldfred on 2020-02-02
Dell issues are often common across many models.

Some others in 5000 series but even others may be similar.
Dell Inspiron 5491
[https://askubuntu.com/questions/1191031/installation-on-new-laptop-dell-inspiron-5491-freezes](https://askubuntu.com/questions/1191031/installation-on-new-laptop-dell-inspiron-5491-freezes)
Dell Precision 5530
[https://ubuntuforums.org/showthread.php?t=2420905](https://ubuntuforums.org/showthread.php?t=2420905)
Dell 5230 with 3 m2 drives.
[https://ubuntuforums.org/showthread.php?t=2406057](https://ubuntuforums.org/showthread.php?t=2406057)
Dell Latitude 5490 M.2 PCIe SSD
[https://ubuntuforums.org/showthread.php?t=2405822](https://ubuntuforums.org/showthread.php?t=2405822)

---

### Post by Autodave on 2020-02-02
Are you attempting to dual boot?  Have you disabled *fast start* in the BIOS?

---

### Post by CelticWarrior on 2020-02-02
> **Autodave said:**
> Are you attempting to dual boot?  Have you disabled *fast start* in the BIOS?

Actually is **Fast Boot** and in UEFI ;)
Fast Startup is another thing, a Windows 8+ feature (that should be disabled as well for a proper dual-boot).

But the thing is: Neither feature has anything to do with the internal drive not being detected.

---

### Post by linuxguiri on 2020-02-02
Thank you so much for your advice and suggestions, CelticWarrior, oldfred, and Autodave. In this particular case, CelticWarrior was right: The problem was that it was in SATA mode.

In case anyone stumbles onto this thread, for completeness, I'll write all of the steps I took to get Ubuntu 19.10 installed alongside Windows 10 on a DELL Latitude 5500 SSD using a USB drive:

**Ubuntu 9.10 Dual Boot USB installation with Windows 10 on DELL Latitude 5500 SSD**
[LIST=1]
[*]Disable Windows Fast Startup (See [https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup) for more details.): 
[*]In Windows, open Power Options
[*]Select &#8220;Choose what the power buttons do&#8221; 
[*]Select &#8220;Change settings that are currently unavailable&#8221; 
[*]Uncheck &#8220;Turn on fast startup&#8221; 
[/LIST]

**Change from SATA to AHCI mode** 
(See [https://www.tenforums.com/customization/104898-switch-raid-ahci.html](https://www.tenforums.com/customization/104898-switch-raid-ahci.html) and [https://support.thinkcritical.com/kb/articles/switch-windows-10-from-raid-ide-to-ahci](https://support.thinkcritical.com/kb/articles/switch-windows-10-from-raid-ide-to-ahci) for more details.): 
[LIST=1]
[*]In Windows, run MSCONFIG (as administrator)
[*]Enable Safe Boot (minimal)
[*]Restart
[*]At DELL boot up screen, press F2 to enter UEFI/BIOS setup.
[*]Select SATA Operation from System Confirmation and change to AHCI
[*]&#8220;Are you sure you would like to continue?&#8221; Yes
[*]Boot in safe mode (happens automatically)
[*]Run MSCONFIG (as administrator) and disable Safe Boot.
[*]Restart Windows
[/LIST]

**Resize Windows partition via Disk Management to allocate space for Ubuntu** 
(See [https://mashtips.com/install-ubuntu-dual-boot-windows10/](https://mashtips.com/install-ubuntu-dual-boot-windows10/) and [https://www.pcsuggest.com/dual-boot-windows-10-and-ubuntu-uefi/](https://www.pcsuggest.com/dual-boot-windows-10-and-ubuntu-uefi/) for more details. Also helpful: [https://partition.toolpie.com/](https://partition.toolpie.com/))

**Install Ubuntu** (see [https://mashtips.com/install-ubuntu-dual-boot-windows10/](https://mashtips.com/install-ubuntu-dual-boot-windows10/) and [https://www.pcsuggest.com/dual-boot-windows-10-and-ubuntu-uefi/](https://www.pcsuggest.com/dual-boot-windows-10-and-ubuntu-uefi/) for more details):
[LIST=1]
[*]Insert bootable Ubuntu USB 
[*]Restart
[*]Press F2 to enter UEFI/BIOS setup
[*]Change Boot Sequence to boot from USB drive first (may need to add USB drive), apply and exit
[*]Select Try Ubuntu and confirm Ubuntu works on system
[*]Click install Ubuntu
[*]At Installation type screen, select &#8220;Something else&#8221; or &#8220;Install Ubuntu alongside Windows 10&#8221; (See [https://mashtips.com/install-ubuntu-dual-boot-windows10/](https://mashtips.com/install-ubuntu-dual-boot-windows10/) and [https://www.techsupportpk.com/2019/10/how-to-install-ubuntu-1910-alongside-windows-10-dual-boot.html](https://www.techsupportpk.com/2019/10/how-to-install-ubuntu-1910-alongside-windows-10-dual-boot.html) for more details. Also helpful: [https://www.convertunits.com/from/GB/to/MB](https://www.convertunits.com/from/GB/to/MB))
[/LIST]

---

