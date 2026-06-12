---
title: "Grub2 installation fails on install onto a WD Blue SN550 NVMe SSD 500GB"
date: 2020-12-04
forum: Installation &amp; Upgrades
---

### Post by ra7411 on 2020-12-04
Error message when install fails: 

"grub installation failed
the "grub-efi-amd64-signed'  package failed to install into /target/. ..... will not boot..."

I'm trying to install Ub18.04 on a m.2 form factor NVMe ssd, and it has failed 3 times, as above.
The mobo is: msi 450 tomahawk. A sata 2.5 form ssd installed and ran for a year just fine.

Quite the pita - I want to shift the 2.5 sata ssd to a 6 yr old machine I use as an auxillary.

Any ideas how to fix this?

Thanks

---

### Post by CelticWarrior on 2020-12-05
Make sure the drive is GTP partitioned before starting the installation.
Make sure you're booting in UEFI mode.

---

### Post by ra7411 on 2020-12-05
> **CelticWarrior said:**
> Make sure the drive is GTP partitioned before starting the installation.
Make sure you're booting in UEFI mode.

Right, checked that the new drive is gpt and that bios was uefi, tried re-install, same error message. 

I've spent as much time as I'm willing to. The nvme gets returned.

Thanks

---

### Post by P-I H on 2020-12-05
Have you tried to install with the old SSD disconnected?

---

### Post by oldfred on 2020-12-05
Ubuntu's Ubiquity only wants to install to first drive.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive. 

If you have ESP, use Boot-Repair & just reinstlal grub to new drive. Grub installs to any drive, it just is Ubiquity that will not.

But if moving drive to another system, you either have to reinstall grub on it, or manually add UEFI boot entry into UEFI for it to boot.
It may boot using fallback/hard drive entry which is at /EFI/Boot/bootx64.efi, but if it does you should reinstall grub to get ubuntu entry into UEFI.
Drive entry like /EFI/Boot/bootx64.efi is how all external drives boot, both Windows & Ubuntu, but obviously different actual files.

Check entry is there.
sudo efibootmgr -v 
sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP.

Also make sure UEFI is updated & SSD firmware is updated.

---

