---
title: "No Grub menu after installation"
date: 2024-09-06
forum: Installation &amp; Upgrades
---

### Post by daanheuvelbeuk on 2024-09-06
Today I reinstalled Ubuntu. I got the message I should restart so the installation could be completed. I did, and Windows was started. No Grub start menu. When I restarted and pressed F11, choose what disk to start from, I came in the Grub menu. Does anyone have an idea?

---

### Post by oldfred on 2024-09-06
What brand/model system?
Most systems work with efibootmgr to change default UEFI boot entry to ubuntu which grub uses when installing.
But a few like HP do not and you have to go into UEFI settings, not the UEFI one time boot key to change boot order.
Some that still want Windows as default, just use the UEFI one time boot key to select ubuntu entry when they want ubuntu rather than grub menu.

New Windows is not always friendly to booting from grub. Grub only can boot working Windows. That also means fast boot must be off, bitlocker must be off & chkdsk not required. UEFI Secure boot may also be an issue as well as some UEFI settings. And Windows turns some of those settings back on with updates. If you want those settings then always boot from UEFI boot menu.

---

### Post by ubfan1 on 2024-09-08
An old toshiba (2012) keeps changing the bootorder putting windows first (in the efibootmgr list).  efibootmgr changes to the order do not persist. The firmware does not allow changing the order of the efI menu boot items, which has Windows first (some machines do allow this). What I found works to get grub to show up is to inactivate the boot items I didn't want, like the windows one  e.g. sudo efibootmgr -A -b xxx .  The order will have the Windows entry first in the efibootmgr order, but not with the * indicating that it's active. This lets the first active one, grub, boot, and it can still boot Windows if needed.

---

### Post by daanheuvelbeuk on 2024-09-09
Thanks for the response. To answer Oldfred, my computer is not a system from a named supplier, but one assembled by a shop in the Netherlands (Clone?). I had to return my system because I had issues with my RAM. I removed my Linux disk for security reasons. As the system now started in the GRUB minimal mode I removed the Ubuntu entry from the Windows bootloader, as described [here]("https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader"). Now the GRUB menu does not appear after Linux installation. 

The GRUB menu worked before.

---

### Post by yancek on 2024-09-09
Some questions which may help to resolve the problem as the information post is not nearly enough.

How old is this computer?
Which release of windows is installed?
Which release of ubuntu is installed?
Are windows and ubuntu on the same physical drive?
Is your installation of ubuntu an EFI install or MBR install?
Is your installation of windows an EFI install or MBR install?

The link in your last post explains removing an Ubuntu entry in both MBR and EFI mode, which did you use?

---

### Post by daanheuvelbeuk on 2024-09-11
> **yancek said:**
> Some questions which may help to resolve the problem as the information post is not nearly enough.

How old is this computer?
Which release of windows is installed?
Which release of ubuntu is installed?
Are windows and ubuntu on the same physical drive?
Is your installation of ubuntu an EFI install or MBR install?
Is your installation of windows an EFI install or MBR install?

The link in your last post explains removing an Ubuntu entry in both MBR and EFI mode, which did you use?

Your questions answered:
How old is this computer? ==> 2 years
Which release of windows is installed? ==> Windows 11
Which release of ubuntu is installed? ==> Ubuntu 24.04 LTS
Are windows and ubuntu on the same physical drive? No. Windows is on a SSD, Ubuntu on a separate HD
Is your installation of ubuntu an EFI install or MBR install? ==> ?
Is your installation of windows an EFI install or MBR install?  ++> ?

I can not answer both questions. If I hazard a guess, EFI, as it is a rather new computer.

The link in your last post explains removing an Ubuntu entry in both MBR and EFI mode, which did you use?
Looking at the code and if memory serves, the Ubuntu entry in the EFI. Would it help when I add the ubuntu directory in the EFI directory?

---

### Post by yancek on 2024-09-11
If your computer is less than 12 years old and has a GPT partition table then windows is installed UEFI mode.  You can obtain this information by booting the Ubuntu install USB and running the command below to list devices/partitions.  You should be able to obtain this information for all drives and can tell which is which as the size is listed in the output and there will be a line in the output showing "Partition Table: gpt" if the devices are GPT.

```
sudo parted -l
```

Check the drive on which you have Ubuntu installed to see if there is an EFI partition there.  If not, check the EFI partition on the windows drive to see if there is an ubuntu directory there.  If Ubuntu was originally an EFI install and you removed the ubuntu directory from the EFI directory it won't boot.

Reinstalling Grub from the live usb install media is possible and an online search should give you a number of options.  The link below has explanations and there is a detailed example about halfway down the page under the heading [B]Run grub-install.  You need to make sure you have the correct device/partition names as they may not be the same as in the example.

[https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition](https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition)
[/B]

---

