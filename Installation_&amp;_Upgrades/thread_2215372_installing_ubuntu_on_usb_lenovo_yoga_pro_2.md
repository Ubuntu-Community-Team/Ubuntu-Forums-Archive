---
title: "installing ubuntu on usb lenovo yoga pro 2"
date: 2014-04-06
forum: Installation &amp; Upgrades
---

### Post by shalom938 on 2014-04-06
Hi
I wanted to install ubuntu 14.4 on usb flash drive, Its lenovo yoga pro 2,I did it before on other computers. on the partition editor I set the grube 2 location to /dev/sdc1 which is the root of the ubuntu install on the usb. the installation is ok but apparently grub2 is somehow installed to the computer hard drive. if I start the computer with the usb unplagged I get a grub2 command line, if the usb is plagged I can choose between windows and ubuntu. but I want to leave the hard drive untouched and keep using windows as normal and boot to linux only when I choose to boot from usb.
Thanks for any help.

---

### Post by Double.J on 2014-04-06
Hi there!

seems that the installer has installed what we used to call stage 1 of grub to the mbr of the hard drive. This is then in turb handing over to the sdc1 partition to find the rest of grub. When the usb is in the machine this path exists, when it is removed, the path does not, and you get the recovery prompt.  

You should be able to fix the situation by running [boot repair]("https://help.ubuntu.com/community/Boot-Repair") and installing the bootloader to /dev/sdc.

to recover windows you'll need to use he recovery partition/ install disc to repair the boot process (bcd) and put windows back in charge of booting. This does mean you'd have to have to either set usb above hdd in the boot order or choose boot select at the bios prompt.

Jj

---

### Post by ubfan1 on 2014-04-06
This is a UEFI machine, so to install to a USB, I use a gpt partition table, have the 300M FAT bootable EFI partition, then add the root and swap (but I usually skip swap on flash usb drives).  Then identify this EFI partition as the location for the bootloader.  That should put the grub files into the EFI partition in /EFI/ubuntu.  However, for removable media like USB, the default bootloader is /EFI/Boot/bootx64.efi, so you need to set that up yourself (or use boot-repair).  For secure boot, copy shim.efi to the bootx64.efi, and have a copy of the signed grubx64.efi in the same directory. The grub.cfg file may be left in /EFI/ubuntu.  This should be a bootable USB.  Now the netbook's hard disk EFI also has the /EFI/ubuntu boot files, but they will not be used (but you can use them for the copy to the USB's EFI).  The netbook's nvram also got changed, so the bootorder no longer has Windows first.  You can change the bootorder with efibootmgr.  use sudo efibootmgr -v  to list the entries, and -o to change them, putting Windows first.

---

