---
title: "How to Prepare A USB that i can boot on several pc's?"
date: 2022-03-18
forum: Installation &amp; Upgrades
---

### Post by tariceagle on 2022-03-18
I have dual boot on an ssd storage. Now i want to prepare another live USB External SSD disc, and use it as external OS on several PC's. But having some problem when i unplug this external storage.

[LIST=1]
[*]First i get 1 USB flash disc with ubuntu iso written with rufus. And get 1 SSD storage which i want to install ubuntu on it.
[*]I pluged in these two USB discs to pc, and boot from the one which iso written with rufus.
[*]Then i install that iso to other USB (sda) port which is my external SSD. I created 1024 mb EFI type partion and other ext4 and fat32 type of partions and tried lots of combinations.
[*]Installations is completed succesfully. And I can choose which ubuntu i want to start on grub screen now.
[*]But when i unplug this external ssd my own ubuntu is not booting. It stuck on the **"gnu grub version 2.04 minimal bash-like line editing is supported "** screen. To reach my own ubuntu i have to plug in this external ssd.
[*]**And this external disc is not listed on the "bios - boot priority panel" neither on my pc nor other pc's.**
[/LIST]

My aim is to create an external disk and boot it on several pc's, with only editing this "bios - boot - boot priority" on each pc. How can i make it undependent to my pc?

---

### Post by grahammechanical on 2022-03-18
> But when i unplug this external ssd my own ubuntu is not booting. It stuck on the **"gnu grub version 2.04 minimal bash-like line editing is supported "** screen. To reach my own ubuntu i have to plug in this external ssd.

I am not sure I understand what you mean by "my own Ubuntu." Is it on an internal drive? What is the drive letter? If we dual boot by installing Ubuntu to another partition or drive whether internal or external, the new install will create a Grub boot menu with its Grub configuration file (grub.cfg) in its own /boot/grub/ directory. Remove that second Ubuntu or disconnect the drive and the first Ubuntu will not boot.

Before disconnecting the external SSD boot into the first Ubuntu and run

```
sudo update-grub
```

Does this produce a Grub menu with the first Ubuntu as the default OS to load? If it does disconnect the second Ubuntu drive (external SSD). Boot into the first Ubuntu and run the above command again. This should remove the second Ubuntu from the Grub menu.

Regards

---

### Post by oldfred on 2022-03-18
You need to reinstall grub, not an update. The update just updates menu.
sudo grub-install

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

If you have ESP - efi system partition (FAT32) on external device, you can just reinstall grub to it.
First you need to change UUID of mount of ESP in fstab.
sudo nano /etc/fstab
to see UUIDs.
lsblk -f
Copy UUID of external drive's ESP to fstab replacing internal drives ESP mount.
Then you can reinstall grub on external drive.

Internal drives boot from an "ubuntu" entry at /EFI/ubuntu.
But external devices boot from /EFI/boot at /EFI/Boot/bootx64.efi. But if full install also need /EFI/ubuntu folder in ESP.
Full install of grub to external will resolve that. 

And an os-prober update of internal's drive grub will also add external drive's grub. But if booting on any other system you boot just like you booted live installer from UEFI boot menu.

---

