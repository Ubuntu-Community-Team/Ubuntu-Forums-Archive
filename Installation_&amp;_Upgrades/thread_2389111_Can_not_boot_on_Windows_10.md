---
title: "Can not boot on Windows 10"
date: 2018-04-11
forum: Installation &amp; Upgrades
---

### Post by pn12345pn on 2018-04-11
Hello, I have installed Ubuntu 17.10 on my 16 GB flash drive, official distribution, installed with USB Installer on erased flash drive. I changed boot to the flash drive in BIOS but I still can not boot it. It still boots Windows. What can I do? I am really frustrated...

Edit: I have ZOTAC ZBOX PI221

---

### Post by yancek on 2018-04-11
Which version of windows do you have installed and is it UEFI or Legacy/MBR install.  Which OS did you use "USB installer" from?

---

### Post by pn12345pn on 2018-04-12
Flash disk is UEFI, Windows (95% sure) Legacy. I used USB Installed on Windows.

---

### Post by oldfred on 2018-04-12
When grub installs in UEFI mode, it wants to install to an ESP - efi system partition on first internal drive usually sda.
And UEFI only boots from ESP & /EFI/Boot/Bootx64.efi from external devices, which grub does not create. I did notice with 18.04, it did create bootx64.efi file & folder.

Boot-Repair may correct that by forcing grub to install to flash drive, I normally have just copied files from sda's ESP to my ESP on flash drive. But you have to partition in advance to have an ESP on external drives.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by LostFarmer on 2018-04-12
[https://www.wiselyguide.com/zotac-announces-stick-zbox-pi220-pi221-windows-10-atom-x5-z8300/](https://www.wiselyguide.com/zotac-announces-stick-zbox-pi220-pi221-windows-10-atom-x5-z8300/)  looks like it boots with a 32bit mode , the 64 bit grub EFI will not work. Likely linux must be 32 bit also , but I do not know.  The link does say it has WIn10 Home 32 bit.

---

