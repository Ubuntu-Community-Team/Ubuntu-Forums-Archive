---
title: "Stuck in GNU GRUB after failing to install Lubuntu in single-boot"
date: 2019-01-14
forum: Installation &amp; Upgrades
---

### Post by m.barisione on 2019-01-14
Hi everybody, I was trying to install Lubuntu 16.04 on a HP Stream 14 in single-boot due to the small hard drive capacity; I've earlier installed (successfully) a version of Bodhi Linux in single-boot and, since I've been encountering several connection issues, I decided to swap to a more solid distribution like Lubuntu. After booting from my USB drive and waiting for the installer to do the job, the installation process showed me an error message telling me that GRUB couldn't be installed and so the entire OS, then I agreed to continue the installation via EFI mode. The installation app crashed and i had to reboot the system: i must add that I also deleted every partition through the installation and ticked the LVM option during the process (don't know if it could help...). Now, I'm stuck into GNU GRUB where minimal BASH-like editing is supported and I don't know really what to do: I looked and looked over the web but still I can't find a clue since I've noticed that every solution deals with dual-booting and then the chance to boot Windows too.

Hope you could help me through it,

Matteo

---

### Post by yancek on 2019-01-14
We will probably need more detailed information for anyone to help so I would suggest you boot the Lubuntu usb/dvd and use the option to Try Lubuntu.  When you get to a Desktop, go to the site below and download the boot repair software.  Use the 2nd option on the page to download from the ppa as it is more current.  Then run boot repair but make sure you select the option to Create BootInfo Summary and do NOT try to make any repairs.  When it finishes, it should give you a link which you can post here and it will have details about your setup.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

