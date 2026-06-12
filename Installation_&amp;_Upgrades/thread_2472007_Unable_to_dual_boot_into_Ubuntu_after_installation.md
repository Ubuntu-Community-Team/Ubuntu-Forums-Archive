---
title: "Unable to dual boot into Ubuntu after installation"
date: 2022-02-15
forum: Installation &amp; Upgrades
---

### Post by parthibans953 on 2022-02-15
Hello,

I have installed ubuntu-20.04.3-desktop-amd64 on my HP Pavilion Windows laptop. But when I boot it always boots to Windows and doesn't give me an option to boot into ubuntu.
When I try to manually boot into Ubuntu using F9 during boot, I get the below error:
"The selected boot device failed. Press enter to continue."
I have tried all the suggested debugging option from online, but no luck.
I don't have legacy boot option in my boot menu and I have selected ubuntu as my default OS while booting.

Below are the logs from ubuntu boot repair software
[https://paste.ubuntu.com/p/T2yYbPZ7zg/](https://paste.ubuntu.com/p/T2yYbPZ7zg/)
[https://paste.ubuntu.com/p/w7N4cpbZJt/](https://paste.ubuntu.com/p/w7N4cpbZJt/)

---

### Post by oldfred on 2022-02-15
I only see one drive, did you add AHCI drivers into Windows and change from RAID or Intel RST to AHCI in UEFI settings?

Every other system besides HP, lets efibootmgr change boot order. Grub when installed uses efibootmgr to make Ubuntu entry first in UEFI boot options.

Everyone with HP, has had to use UEFI settings (not UEFI boot menu) to change boot order. Or always use UEFI boot menu to choose Ubuntu.
Many with HP also have had to update HP's UEFI firmware and SSD's firmware.

What model HP? 
Some have posted more details, by model. Or similar models.

HP 17-BY4063CL Laptop shows UEFI screens, needed 21.04 since new Intel chip
[https://ubuntuforums.org/showthread.php?t=2462045](https://ubuntuforums.org/showthread.php?t=2462045)
hp 250 g3  Change boot order in UEFI settings
[https://ubuntuforums.org/showthread.php?t=2467077](https://ubuntuforums.org/showthread.php?t=2467077)
HP Envy - use UEFI to change boot order
[https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun](https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun)
HP 15 disable Optane
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483) & 
[https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10](https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10)

---

