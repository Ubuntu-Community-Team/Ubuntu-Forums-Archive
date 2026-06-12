---
title: "Ubuntu (and GRUB) won't start (loop reboot)"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by spivaktar on 2018-04-29
Hi! I am here asking for help with Ubuntu boot. I tried installing the system in auto mode with total format of SSD but it didn't work (everything is running in uefi mode). Previously I had a Windows 10 on this computer and I just formatted the disk using Ubuntu Live CD. Then I manually created a fat32 partition with "boot" and "esp" flags using GParted but it didn't work as well. The GRUB just won't start and system is in loop reboot condition. I also tried a Boot Repair tool ([http://paste.ubuntu.com/p/tHZP5MhWTV/](http://paste.ubuntu.com/p/tHZP5MhWTV/)) but despite it says the boot is fixed it actually is not. I really don't know what to do with this thing and I guess that the problem is with partition table but I don't know a thing about them. I would extremely appreciate any kind of help from you guys.

---

### Post by oldfred on 2018-04-29
It looks like a normal UEFI install.
Some systems do not like to boot anything other than "Windows Boot Manager" by description.

First lists of UEFI entries showed many duplicate ubuntu entries, but final one only shows the one entry? Did it houseclean itself?

Can you boot ubuntu entry from UEFI boot menu.
Can you boot hard drive entry? Looks like it may be ATA HDD0. 
Do you have the other drives or is that just some defaults in its UEFI?

Since only booting Ubuntu one work around is to create an entry with Windows description but Ubuntu/grub's shim boot file. It checks description but not actual boot file?

       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

Multiple other work arounds in link in my signature.

Have you updated UEFI to latest version for your system?

Other Lenovo:
 Lenovo y50-70 use rEFInd
[https://askubuntu.com/questions/987409/ubuntu-boot-failed-cant-modify-bios-setup-to-remove-secure-boot](https://askubuntu.com/questions/987409/ubuntu-boot-failed-cant-modify-bios-setup-to-remove-secure-boot)
Lenovo boot screen can be accessed by Fn + F2 keys, boot device selection by Fn + F12.

---

