---
title: "Trying to install Ubuntu in an external SSD"
date: 2021-03-29
forum: Installation &amp; Upgrades
---

### Post by oden99 on 2021-03-29
I Want to install ubuntu at a Samsung p7 SSD external drive.

I created an immage that boots and runs on another USB stick, booting from that stick and choosing "install Ubuntu (20.04 LTS)

Option "do something else"

Selecting my Samsung P7
Creating a partition Fat 32 "/MDISK" gets marked for format (sdb1)
Creating an ext4 partition with mount point / (also marked for formating) (sdb2)
Creating a swap area about 8GB in size (no mark for format)
Setting the boot option to the samsung SSD drive (sdb) in this case.

I click continue  and gets a warning about unmounting my CD drive don't work ?!
Letting ubuntu try to do this and clicks continue.

Then all get stuck in "identifying file system (waited 72 hrs at the most)

What is going on ?

I need advice on how to get pass this "stuck thing".

Suggestions would be much apreciated..

Added info the  samsung drive are 500GB in size

---

### Post by CelticWarrior on 2021-03-29
Welcome.

You need to select type EFI for the fat32 partition.
You can have a swap partition but there's no need, Ubuntu uses a swapfile by default now.

---

### Post by oldfred on 2021-03-29
If UEFI install, the selection of location of boot loader is not used. It just defaults to first drive's ESP -  efi system partition (FAT32), usually internal drive.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

I do check mounts while installing and often have issues with /isodevice. Since I use toram parameter the entire installer is in RAM, so reading isodevice is not then required. 

# Required as /isodevice usually mounts to a partition and installer does not correctly unmount
sudo umount -lrf /isodevice
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216)
Says to use toram boot

---

### Post by slickymaster on 2021-03-29
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by oden99 on 2021-03-29
Thanx for the reply..Ofcource I missed that one..it comes back now. Boot and EFI was not set.. I try again then. Let's hope it goes without flawf this time..

---

