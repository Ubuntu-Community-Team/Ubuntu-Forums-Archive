---
title: "About boot loader"
date: 2017-08-21
forum: Installation &amp; Upgrades
---

### Post by rrob3rtt on 2017-08-21
If I install multiple distros should I set the "Install boot loader on" option to the hard drive I am installing to or set it to the same hard drive every time I install a new distro. This will be for multiple distros on 3 different hard drives. What I mean is that I dont understand if each distro needs its own boot loader or should their be only one boot loader on one drive. I hope I am making myself clear. Thank you.

---

### Post by oldfred on 2017-08-21
UEFI or BIOS? 

With BIOS I always had a different boot loader on every drive, usually the one for most recent install on that drive. You only get a choice on where to install boot loader with the Something Else install option. But set in BIOS my default install and used link below to simplify grub menu by turning off os-prober and using my own 40_custom boot stanza.

While UEFI will offer the choice, it does not work. Grub only installs to the ESP - efi system partition on drive seen as sda. I still include an ESP on every drive and copy boot files from sda's ESP to each installs ESP just in case I later disconnect original sda and want boot files on that drive. But that is more of a backup than a requirement.

If only booting Ubuntu, I suggest using gpt partitioning. And if drive will ever be on an UEFI system include an ESP as first partition. But if BIOS hardware, you need a bios_grub partition. And if dual booting on same drive as Windows in BIOS mode, you must use MBR(msdos) partitioning.

If UEFI see link in my signature.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

