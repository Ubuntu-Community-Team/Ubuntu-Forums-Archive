---
title: "is t not possible to install in usb hdd ?"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2014-04-26
i am trying to install 14.04 lts in usb hdd.
at the end of nstall installer crshed and made a report for devs. and sent.
i am now trying again and to get the error report
will come back again with results.
any advice welcome.

post installation trigger libc bin failed and installer crashed.

---

### Post by ramaswamyps on 2014-04-26
this is the error screen i got.
i have spent lot of money and time for getting dvds and usb sticks to try and install this in my toshiba satellite c855d-s5232 laptop.
dvds i got does not work saying pwer calibratio area error. 2 packs f 10 dvd each just wasted.
anyways it looks like i cannot install this 64 bit ubuntu 14.04 lts distro. already 2 attempts failed.

---

### Post by ubfan1 on 2014-04-27
I should be possible to install 14.04 to a usb on your Toshiba C855.  A few tips from my experience on an S855:
1)  Do not try to use the usb3 ports.  I could not successfully install (or even copy an install to a USB3 stick in a USB3 port).  Once installed, the stick runs fine in the USB3 however.  
2)  I used gpt partitioning, and put a 300M FAT32 EFI partition on my 8G stick, no swap, rest just for /.
3) Identify the USB's EFI partition as the location for the bootloader installation.  Old problem with 12.10 was to ignore the device, and put the bootloaders onto the hard disk's EFI.
4) Secure boot should work, but is not needed. Definitely keep the UEFI mode.  Note that Windows will not boot from grub even with the correct chainloader paths with secure boot on.  
5) When the installation is done, the bootloader you installed into the USB's EFI  /EFI/ubuntu directory should be copied to /EFI/Boot/bootx64.efi.  If you are doing this with secure boot on, that would be the shim.efi, if not, it would be the unsigned grubx64.efi.  If you are using shim.efi, you also need a copy of the signed grubx64.efi in /EFI/Boot.  
6) Ideally, no changes will be made in your laptop's nvram, the existing USB entry should be enough to boot the stick -- put the USB first in the boot order.  You can select how to boot with F12, then select usb or hdd for windows.
run the md5sum hashcheck on the downloaded iso, and then use unetbootin on windows to create a USB install media (if you DVDs are really not usable).
7)USB to USB installs still confuse grub sometimes, and the grub.cfg file has some wrong devices (miscounted because the install media adds a device when the file was created).  You might need to edit the grub boot the first time (inst on screen), and reduce the disk number/letter by one. UUIDs are OK when they are used.  After first boot, immediately run sudo update-grub to fix things.

---

### Post by ramaswamyps on 2014-04-28
i learnt it the hard way. i use a usb wireless mouse , i used a usb stick installer , and the usb hdd. i see how it fails.
now i made a dvd and installed from that to the usb hdd. it worked nicely. i saw your reply just after the installation. i had a nagging doubt about the 3 usb used all at a time.
i am posting this from the new install.
thanks for the reply 
ubfan1  :)

---

