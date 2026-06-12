---
title: "unstall on a 32g flashdrive"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by jtmedin on 2013-12-21
Is it possibel to install ubuntu on a 32g thumbdrive? My intention is to plug in the flashdrive on a usb 3 port whenever i want to run ubuntu. Then remove the flashdrive when i want to use win8. TIA

---

### Post by sanderj on 2013-12-21
Yes, but use the live-usb install method. Not a real install as that will be very slow.

---

### Post by Photobug on 2013-12-21
Use Unetbootin do a search for it.  It is a program that will create a bootable live drive.  Make sure you create a live drive as only a live drive will keep the configuration changes you make to the system on the thumb drive.  You will also use this live drive to install the OS to your computer s hard drive when you get frustrated with the hassle of the thumb drive.  That's what I did after about a week.  Keep the thumb drive though as it is a great tool to troubleshoot with.

---

### Post by ubfan1 on 2013-12-21
C.S Cameron has posted several comparisons of live-media vs full install on askubuntu.com.  There are various optimizations possible on a full install which greatly improve the responsiveness -- most boil down to moving as much into memory as possible, like /tmp, /var/log, /var/cache/apt/archives, and your browser cache.  Alignment of the filesystem with the underlying erase block size is done with most of the current defaults, like starting the first partition on block 2048, but if you add more partitions, using a 4m alignment cannot hurt.  I had trouble writing to a USB3, and don't know if it was the stick, the machine, or even the usb driver, but once I copied off a usb2 stick to the usb3, things worked fine.  On a UEFI machine, which I assume you have since you specified W8, you should try to keep the same mode as Windows uses -- UEFI probably, secure boot if necessary to boot Windows.  you can set the USB stick up with gpt partitioning, and make a 300M EFI partition for the bootloaders.  Install specifying that PARTITION as the bootloader location, since just the USB3 device will not work in this case (It will go to the hard disk's EFI partition). Then you will have to manually fix the "remote media" for booting, since the default bootloader is /EFI/Boot/bootx64.efi, not whatever got copied into /EFI/ubuntu.  For secure boot, copy the /EFI/ubuntu/grubx64.efi to /EFI/Boot, and copy /EFI/ubuntu/shim.efi to /EFI/Boot/bootx64.efi (renaming in the copy). For no secure boot, just copy grubx64.efi to the bootx64.efi in /EFI/Boot. Your grub.cfg file should stay in the /EFI/ubuntu directory, where it will be picked up.  I recommend backing up your hard disk's EFI files too, since lots of things can go wrong, and you might need to restore them.  The usb install logically needs no nvram modifications and nothing should be written onto the hard disk, but I find odd things still happen when installing/updating USBs.  You can even copy your Windows boot files onto the USB as a backup for them, and they should be usable too.

---

