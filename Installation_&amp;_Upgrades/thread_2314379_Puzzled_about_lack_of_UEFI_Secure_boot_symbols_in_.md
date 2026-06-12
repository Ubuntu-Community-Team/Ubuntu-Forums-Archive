---
title: "Puzzled about lack of UEFI Secure boot symbols in BIOS screen"
date: 2016-02-20
forum: Installation &amp; Upgrades
---

### Post by phoenix1963 on 2016-02-20
Hi, I've installed 15.10 on a new home built PC.
However, in the (Asus) BIOS screen the Live USB shows as UEFI, but the main boot drive shows no UEFI symbol.

Secure boot in MS mode is shown as "on".

Has Ubuntu installed in Secure boot UEFI mode or not?

Maybe the SSD I'm using is not UEFI compatible (Kingston SV300S37A60G)?

How do I know what's going on?

phoenix1963

---

### Post by oldfred on 2016-02-20
If you install in UEFI boot mode there are the standard unsigned kernels & grub files or the signed versions for UEFI with secure boot.
But if you installed in BIOS boot mode there is no secure boot setting.
Three ways you can install or boot. UEFI, UEFI with secure boot, and BIOS. Only one includes secure boot.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

My Asus motherboard made it difficult to boot in UEFI mode at all. 
It had settings for Windows & Other, and I believe other was not secure boot and Windows was. But I do not use secure boot.

---

### Post by sudodus on 2016-02-20
When running Ubuntu, you can use the following command line in a terminal window to check if the computer is running in UEFI or BIOS mode

```
test -d /sys/firmware/efi && echo efi || echo bios
```

See more about UEFI at the following link (and links from it),

[Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by phoenix1963 on 2016-02-21
Thanks for the links to a lot of info, it'll take a while to figure out which is the crucial bit.

Sudodus: it returns "bios", so it's booting the old fashioned way. But when I try the same command on my live-usb I get "efi", so presumably the image I've used is EFI bootable (i.e. signed).

So reading through some of the links, I suspect I may simply need to change the configuration files to get it booting the UEFI way. Hopefully this won't mean putting the PKs into the BIOS...

My starting point was originally [https://linuxconfig.org/legacy-bios-uefi-and-secureboot-ready-ubuntu-live-image-customization]("https://linuxconfig.org/legacy-bios-uefi-and-secureboot-ready-ubuntu-live-image-customization"), a good article, but I fell down at this stage:

```
sudo xorriso -as mkisofs -isohybrid-mbr isolinux/isohdpfx.bin \ 
-c isolinux/boot.cat -b isolinux/isolinux.bin -no-emul-boot -boot-load-size 4 \
-boot-info-table -eltorito-alt-boot -e boot/grub/efi.img -no-emul-boot \
-isohybrid-gpt-basdat -o ../custom-ubuntu.iso .
```

because my xorriso doesn't find "isohybrid-gpt-basdat". So I just used the default iso instead.

phoenix1963

---

### Post by sudodus on 2016-02-21
Some computers can be set to boot either in UEFI mode or BIOS mode depending on what system you are booting. I have a Lenovo Thinkpad with such a BIOS/UEFI menu, and I can select which mode is preferred if the system can be booted in both modes. It can also be set to boot only in UEFI mode or BIOS mode. I suggest that you check your BIOS/UEFI menus, if it is possible to force it into one of the modes.

'Signed' means that it works with secure boot. You can boot an unsigned system in UEFI mode too, but not with secure boot.

---

### Post by oldfred on 2016-02-21
Why are you going thru the build your own customized ISO when you can just install with the standard 64 bit ISO.

       You will need to use the 64 bit version of 14.04 or 15.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need Windows  fast start up (hibernation) and UEFI/BIOS fast boot quick boot UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


 Ubuntu UEFI install ISO
Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by phoenix1963 on 2016-05-21
I've solved it all by point 2 in my recent post [http://http://ubuntuforums.org/showthread.php?t=2325340]("http://ubuntuforums.org/showthread.php?t=2325340").

Many thanks to Rod of Rod's books.

phoenix1963

---

