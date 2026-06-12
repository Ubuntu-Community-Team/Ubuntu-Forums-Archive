---
title: "Kubuntu UEFI device for bootloader installation"
date: 2016-07-08
forum: Installation &amp; Upgrades
---

### Post by sam81 on 2016-07-08
I'm trying to install Kubuntu 16.04 in a dual boot configuration with Windows 10. Windows 10 is installed in UEFI mode, and the BIOS is setup to allow only UEFI (legacy boot options are disabled). I disabled secure boot. I chose manual partitioning and I'm at the partitioning step. At this point I'm asked the device for boot loader installation (see image attached).[ATTACH=CONFIG]270014[/ATTACH]

which one should I chose? According to this guide [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

"in a UEFI-mode installation, Ubuntu will not ask you where to install the boot loader. If it does, or if it complains about the lack of a BIOS Boot Partition, you've probably accidentally booted in BIOS/CSM/legacy mode."

it doesn't seem possible that I've booted in BIOS/CSM/legacy mode because those options were disabled in the BIOS. What should I do? I've seen tutorials saying to choose the existing Windows 10 EFI partition as the device for boot loader installation. Is this safe?

---

### Post by ubfan1 on 2016-07-08
Well, in a UEFI install, it still asks, but then ignores what you enter and just puts the grub bootloaders into a new directory in the existing efi partition on the first disk.  Usually, this first disk is sda, but in your case, it's not, it's the nvme0n1p1 device.  Don't know it that will cause any problems, since sda does not even have an efi.  Anyway, there is no problem putting the grub bootloaders into the existing Windows efi partition, since the bootloaders will be put into a separate directory, ubuntu, and will not overwrite anything.

---

### Post by sam81 on 2016-07-08
many thanks for the info

---

### Post by oldfred on 2016-07-08
Grub needs to install to the NVMe drive.
But I have installed to flash drives & sdb drives and wanted grub to install to those drives which I had created an ESP - efi system partition and it still overwrote my /EFI/ubuntu on sda.

But since your NVMe drive is your boot drive, grub should install to it. It will be interesting if it does correctly. And if not a bug report needs to be made.

Lets see what happends, but if it has to have sda, then we may have to create an ESP on sda.

---

### Post by sam81 on 2016-07-09
Thanks for the info and for pointing me to the UEFI thread. I left the laptop at the office so I can't try now but I definitely will. For the device for bootloader installation the installer gives the option of choosing "/dev/nvm0n1" (the NVMe drive), and "/dev/nvm0n1p1" (the EFI partition of the NVMe drive). I suppose that either choice should be fine and should lead to the same outcome, that is the bootloader  should install on the EFI partition of the NVMe drive right?

---

### Post by oldfred on 2016-07-09
I have many times chosen anything other than sda as I have installs on other drives than sda, but every time it has installed to the ESP on sda overwriting my /EFI/ubuntu and since sda has the /EFI/ubuntu for my main working install, I quickly learned to back up that also.

But for my full install to flash drives, I was able to copy files from sda to sdc's ESP and rename to allow external to boot.

---

### Post by sam81 on 2016-07-20
I did the installation and everything went fine. For the device for bootloader installation I chose "/dev/nvm0n1p1" and the bootloader was installed in the EFI partition alongside the Microsoft bootloader. For the record, in the end I installed KDE Neon rather than Kubuntu, but I suppose the process would be very similar on Kubuntu. The default boot manager is now the KDE neon boot manager, and it gives me an option to boot into Windows. Thanks again for the help.

---

