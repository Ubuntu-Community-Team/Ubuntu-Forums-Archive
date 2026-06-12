---
title: "Windows crash after installing Ubuntu 16/ no bootable device"
date: 2018-09-12
forum: Installation &amp; Upgrades
---

### Post by sawezx on 2018-09-12
Hey there,
I installed Ubuntu by USB disk, for dual boot with Windows 10, on extended partition, I made /, /home and efi system partition, because without efi partition instalation crushes on installing grub2 point, 
I have 5 years old Hp pavilion g7 and guess it's not UEFI. 
I used option "something else" during the installation. 
Before installation I turned off Legacy support and Secure boot (maybe it was a fault) after installing Ubuntu I faced with problem like "no bootable device insert boot disk and press any key" and now I can't use any of Operating system
I tried to change Legacy support and Secure boot many times, but it was unsuccessful 
Can someone explain why it happened and provide a solution if exist

---

### Post by yancek on 2018-09-12
Was windows 10 pre-installed?  If it was, it was almost certainly UEFI and it would be necessary to install Ubuntu UEFI.  If windows is not UEFI, then you would need to install Ubuntu in Legacy mode also.  I would suggest that you read through the Ubuntu documentation on dual booting windows 10/Ubuntu UEFI at the Ubuntu site link below.  YOu might also boot the Ubuntu install usb and from a terminal, run the following command:  sudo parted -l (Lower case Letter L in the command).  I believe you need your EFI partition on a primary and it needs to be FAT32.  

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

