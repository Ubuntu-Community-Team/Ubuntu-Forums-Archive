---
title: "Unable to install Ubuntu 16.04.2 on XPS 13-grub-install /dev/nvme0n1 failed"
date: 2017-03-23
forum: Installation &amp; Upgrades
---

### Post by shahidj077 on 2017-03-23
Hi, I am trying to dual boot Ubuntu 16.04.2 LTS and windows 10 on Dell XPS 13 (9350) laptop. Windows 10 came pre-installed and I am installing Ubuntu via bootable USB stick using Rufus.  I have tried both the "install alongside Windows option" and manual configuration (Something else) as well, In both cases it installs more than halfway, then prompts the error:

```

Unable to install GRUB in /dev/nvme0n1
Executing 'grub-install /dev/nvme0n1 failed
This is a fatal error
```

_Installation and Error Pics:_

[https://i.stack.imgur.com/da9PC.jpg](https://i.stack.imgur.com/da9PC.jpg)


I have the following configurations set in BIOS (Version: Dell Inc. 1.4.13, 28-Dec-16):

```
 UEFI Boot, Enable UEFI Network Stack, AHCI, Secure Boot disabled.
```
  

_BIOS Config Pics:_

[URL="https://i.stack.imgur.com/kCGMC.jpg"]https://i.stack.imgur.com/kCGMC.jpg
[/URL]
I have also tried boot-repair

[http://pastebin.com/5dQeqBwh](http://pastebin.com/5dQeqBwh)

Any help would be greatly appreciated. Thank you!

---

### Post by vanadium on 2017-03-23
This problem seems similar to yours, [https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)

---

### Post by oldfred on 2017-03-23
I have seen some with Dell that have to have the legacy boot option checked or on to work, but still install in UEFI boot mode. Most systems must have the legacy/CSM/BIOS option off to install in UEFI mode.

You should also make sure you have newest UEFI from Dell and NVMe drive's firmware.

Another user with XPS and NVMe drive.
       Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)

---

### Post by shahidj077 on 2017-03-24
This solved the issue :

[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)

---

