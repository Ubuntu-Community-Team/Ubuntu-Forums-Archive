---
title: "efi/boot and boot partiton question"
date: 2015-11-30
forum: Installation &amp; Upgrades
---

### Post by ags40 on 2015-11-30
I want to install Kubuntu 14.04 with its own boot partition, the question is: do I have to create a separate efi/boot also? If so how large is perfect? Thank you very much.

---

### Post by Vladlenin5000 on 2015-11-30
No, only one ESP (EFI partition) is needed.

---

### Post by oldfred on 2015-11-30
Most desktop installs do not need a /boot partition and are a bit easier to manage without it. But if using full drive LVM or LVM with encryption then you have to have the /boot partition.

Do not confuse an ESP - efi system partition with a /boot partition, they are different.
You can only have one ESP per device. And drive must be gpt partitioned for UEFI boot. With Ubuntu you can also boot from gpt with BIOS, but Windows only boots from gpt with UEFI.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

### Post by ags40 on 2015-12-01
Thank you very much. Now I've learned something new.

---

