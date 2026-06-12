---
title: "Problem with installation Linux Mint/Ubuntu/Elementary OS"
date: 2019-11-20
forum: Installation &amp; Upgrades
---

### Post by jantex69 on 2019-11-20
Hello. I have Dell XPS 13 9350, i5 6200, 8GB, 120 SSD(My disk is divided by C and D(Empty)). I want to boot my second OS (the first one is Win 10). A have tried to install Linux Mint/Ubuntu/Elementary OS and I got the same problem. So at the beginning of installing, after choosing the language i have the dialog called "Updates and other software" where I need to choose the full installing or minimal. After that, I press next and the dialog stucks, mouse is spinning around and nothing goes. Who knows, what the problem is?

---

### Post by oldfred on 2019-11-20
Dell typically requires UEFI update, SSD firmware update.
Install AHCI drivers into Windows and change UEFI setting from RAID/Intel RST to AHCI.
And in Windows make sure fast start up is off.

If you almost get to partitioning screen it probably is the AHCI setting, but other changes often required.

Issues with Dell are across many models, so similar:
Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)
[https://askubuntu.com/questions/696413/ubuntu-installer-cant-find-any-disk-on-dell-xps-13-9350/743329#743329](https://askubuntu.com/questions/696413/ubuntu-installer-cant-find-any-disk-on-dell-xps-13-9350/743329#743329)

How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

General UEFI install instructions in link in my signature.

---

### Post by jantex69 on 2019-11-21
Actually, I've already updated all drivers which are required, and the problem is not dissapear.

---

### Post by oldfred on 2019-11-21
Are drives set to AHCI in UEFI settings?

---

