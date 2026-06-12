---
title: "Boot Repair Problems"
date: 2024-01-10
forum: Installation &amp; Upgrades
---

### Post by gyrocoptic on 2024-01-10
Hi,

I have a dual boot windows 11 and Proxmox VE system.  After re-installing Proxmox VE, I could only boot PVE by selecting it in the UEFI.  In an attempt to perform a Grub repair I booted to the "Boot Repair" live cd and selected "Recommended repair".  I executed a bunch of commands as instructed and clicked "Forward".  I was then confronted with a warning dialog... 

"GRUB is still present.  Please try again.  (purge grub packages from /mnt/boot-sav/mapper/pve-root)"  

I have rebooted to the live cd and re-run the Boot Repair with the same results each time.

Here is the link to the boot info summary it provided...

[http://*******.us/upW9Vy](http://*******.us/upW9Vy)  (for some reason it replaces "s-p-r-u-n-g-e" with *******)  (why?)

Any help or insights are greatly appreciated.

---

### Post by oldfred on 2024-01-10
Do not know proxmox nor LVM.

But it looks like you have installed grub twice, once in UEFI mode & once in BIOS boot mode.
UEFI requires an ESP - efi system partition.
BIOS boot on gpt partitioned drives requires a bios_grub partition.
But you have both and only one is required, based on how you installed grub and then have set default boot mode of your system UEFI  or BIOS.
You may need to totally reinstall grub and make sure UEFI is set to boot in UEFI boot mode with Secure Boot off. Full reinstall of grub adds same UEFI boot entry shown below and may be more correct.

Since UEFI better to use UEFI. To add UEFI boot entry:
sudo efibootmgr -c -L "proxmox" -l "\EFI\proxmox\grubx64.efi" -d /dev/nvme0n1 -p 2
for details see:
man efibootmgr

Shimx64.efi works for both UEFI and UEFI secure boot. I do not have Secure boot on & use shimx64.efi. Report is not showing shimx64.efi and only grubx64.efi. So If an UEFI update turns Secure Boot on, you may be be able to boot until you turn it off. Windows may update UEFI with other updates.

---

