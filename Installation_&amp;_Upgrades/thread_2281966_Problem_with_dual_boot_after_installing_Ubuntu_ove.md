---
title: "Problem with dual boot after installing Ubuntu over Fedora"
date: 2015-06-11
forum: Installation &amp; Upgrades
---

### Post by zdaniel-gp on 2015-06-11
Hi guys!

I'm having a problem since I decided to change from Fedora 20 to Ubuntu 14.04. At first, it didn't detected any OS installed, so I manually removed Fedora's partitions and setup with a ext4 + swap partitions.

Now I can't boot into my Windows 8. I tried several settings with grub, it looks like there's a windows EFI boot file inside /boot/efi folder, but whatever settings I use with grub, when I try to select the OS, nothing happens.. just a black page for a moment and it returns to the OS selection screen.

Here is my boot-repair log: [http://paste.ubuntu.com/11681804/](http://paste.ubuntu.com/11681804/)

and also the screenshot of how are my partitions today:

[ATTACH=CONFIG]262518[/ATTACH]



If anyone can help me suggesting what I should do, it'd be awesome.

Thanks!

---

### Post by oldfred on 2015-06-11
I believe UEFI allows FAT16 for external drives and some very early versions of grub did use FAT16 for a new efi partition. But not sure if Windows can use that as FAT32 is supposed to be the efi partition for internal drives.

I would fully back up the efi partition, delete it, and create a new FAT32 partition with the boot flag so it is flagged as the ESP - efi system partition. Then copy files back, no special install should be required.

You also have some old UEFI boot entires and some duplicates in you UEFI NVRAM settings. You may want to house clean with efibootmgr. Details in link in my signature.

Since Boot-Repair was asking for a bios_grub partition, you must have booted it in CSM mode not UEFI mode. Be sure to boot in UEFI mode as your installs on the hard drive are UEFI. You should have two choices to boot live installer flash drive. Or Boot-Repair also does not see a FAT32 partition as an efi partition.

---

