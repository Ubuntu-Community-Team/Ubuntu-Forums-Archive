---
title: "Asus X401U + Lubuntu as a single OS (booting error)"
date: 2014-11-17
forum: Installation &amp; Upgrades
---

### Post by tauri-alas on 2014-11-17
Hi

I have a Asus X401U laptop (which had preinstalled Windows 8 on it). I used [www.pendrivelinux.com](www.pendrivelinux.com) to create bootable USB stick with Lubuntu and afterwards tried to install Lubuntu as the only OS to my laptop (changed drive partitions by hand after disabling Secure Boot in BIOS). Now if I restart my computer the HDD will not be booting and instead BIOS opens again. Under BOOT section there is no HDD nor Flash Drive option to choose as first booting device (actually the selection list is empty). How could I set up my computer so it would boot from HDD?

---

### Post by ajgreeny on 2014-11-17
This is probably a UEFI problem; I suspect you may have the system setup with UEFI but, if you made no changes, installed in legacy BIOS mode.

See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for all the info, and hopefully a solution.  If this is not the answer come back again and ask for more help.

---

### Post by oldfred on 2014-11-17
Do you still have secure boot on, and installed in UEFI non-secure boot mode. Or in BIOS mode as that also is not secure boot?

        Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)

---

