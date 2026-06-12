---
title: "Trying to install full ubuntu to a flash drive on my surface book"
date: 2017-02-11
forum: Installation &amp; Upgrades
---

### Post by sisama on 2017-02-11
I am trying to install a full ubuntu to a 32G flash drive and I have a surface book. When I try to select the location to install ubuntu, instead of showing dev/sda, dev/sdc, dev/sdb, it shows 
dev/nvme0n1p1 efi
dev/nvme0n1p2 
and so on...

I am wondering which location should I choose? Is there anything wrong with it?

Thank you very much

---

### Post by oldfred on 2017-02-11
Your NVMe drive is the internal SSD on your system.

Are you wanting to install from a small flash drive installer to a larger flash drive? Or are you installing to the NVMe drive?

---

### Post by sisama on 2017-02-12
I want to install it to a flash drive instead of my ssd. Can I stall it to the same usb I used to boot ubuntu? 
Thank you for your reply.

---

### Post by sudodus on 2017-02-12
Yes, if you use a RAM drive (and unmount the USB pendrive). Is can be done manually with the boot option **toram** according to the following links.

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

[How to unmount a live DVD/USB?](https://askubuntu.com/questions/854527/how-to-unmount-a-live-dvd-usb)

[Can Ubuntu be installed to the pendrive it was booted from?](https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from)

---

### Post by oldfred on 2017-02-12
Probably best to keep flash drive installer.
If install to flash drive does not boot, then you have no way to fix it as you need flash drive in live mode to run repairs.

Also will you be installing in UEFI or BIOS boot mode? If UEFI be sure to partition in advance, use gpt and include the ESP- efi system partition which is formatted FAT32 with boot flag.

Full UEFI install to any external drive is not normally configured correctly by grub. There are two issues, both best if fixed while booted in installer and before rebooting.
Grub only installs to ESP - efi system partition on drive seen as sda. Not sure if your NVMe drives further confuse it as some have worked and others have had issues.
UEFI only boots from /EFI/Boot/bootx64.efi, but grub does not create that file.

Best to just copy /EFI/ubuntu from internal drive to flash drive. Then copy again from internal drive to /EFI/Boot and rename shimx64.efi to bootx64.efi. You have to have both folders as full install grub expects more files in /EFI/ubuntu. 

My 32GB flash drive with half for Ubuntu and half for data.
```
Disk /dev/sdc: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      20.5kB  500MB   500MB   fat32        esp_usb  boot, esp
 2      500MB   501MB   1049kB                        bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         data32   msftdata

```
I often suggest 300 to 300MB for ESP, and used 500MB above. But with flash drive I will not be experimenting a lot and 100MB is probably more appropriate.

---

