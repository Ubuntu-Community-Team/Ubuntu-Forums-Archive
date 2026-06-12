---
title: "Windows 10 Bootable USB on Ubuntu"
date: 2019-05-18
forum: Installation &amp; Upgrades
---

### Post by norbertk237 on 2019-05-18
I'm trying to create a bootable USB for installing Windows 10. I have followed the instructions on here ([https://www.linuxbabe.com/ubuntu/easily-create-windows-10-bootable-usb-ubuntu](https://www.linuxbabe.com/ubuntu/easily-create-windows-10-bootable-usb-ubuntu)) and also tried using WoeUSB. When the USB is connected to the laptop (XPS 13), I get a message saying System BootOrder not found. Initialising defaults. They recommend here ([https://askubuntu.com/questions/1042747/system-bootorder-not-found](https://askubuntu.com/questions/1042747/system-bootorder-not-found)) to turn on Secure Boot and then add some files as secure for execution. I couldn't find any place to specify those files, but I do have similar settings automatically set up:
- ubuntu with \EFI\ubuntu\shimx64.efi
- uefi with EFI\boot\bootx64 (no starting slash)

The first one is the currently running Ubuntu, the second is coming from (I'm guessing) some kind of internal storage that dell restores automatically. If I delete either of these boot options, they are automatically added back.

As the USB is a windows installer, I wouldn't expect it to have \EFI\ubuntu\shimx64.efi but the other file should exist. 

The output from running `efibootmgr -v`:
```
BootCurrent: 0000Timeout: 2 seconds
BootOrder: 0000,0001
Boot0000* ubuntu	HD(1,GPT,00176181-e715-483d-8a69-a5d7e179cb60,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* UEFI: PC300 NVMe SK hynix 256GB, Partition 1	HD(1,GPT,00176181-e715-483d-8a69-a5d7e179cb60,0x800,0x100000)/File(EFI\boot\bootx64.efi)..BO
```

What do I need to do to create a bootable usb that I can use to install Windows? I remember this being so simple, also I used Windows 10 April 2018, because I read about the October release containing a large file which requires NTFS partition and that causes problems with some of the systems. I also tried that, though, without any success.

---

### Post by oldfred on 2019-05-18
UEFI only boots from /EFI/Boot/bootx64.efi from a FAT32 formatted partition with the boot or esp flag on external devices. They then went back and added that as a boot option/fallback option for internal drives. Windows version of bootx64.efi is a copy or version of its bootmgfw.efi.

Your flash drive will not be shown in efibootmgr -v as a permanent entry, but if flash drive correctly configured, it should show another boot option in the one time UEFI boot key, often f12 or f10. With Ubuntu live installer's default configuration for both BIOS & UEFI, you normally get two entries in UEFI boot menu, one UEFI and one BIOS.

I believe this also works for Windows.
If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash drive partition & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)

Windows bootable USB from Ubuntu BIOS or UEFI, uses grub for BIOS boot.
[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)
[http://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu](http://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu)

---

### Post by norbertk237 on 2019-05-18
The first link says that if I have the file /efi/boot/bootx64.efi, then it should already work. I checked and the file is there but it doesn't work. The second link uses WoeUSB which I've already tried (as mentioned before), it still doesn't work. I went through the third link, the boot flag wasn't set; however, I get the impression from reading about this online that it is not necessary for UEFI. I set it anyway and tried to boot from it, still no success and the same error message.

---

### Post by oldfred on 2019-05-18
Many partition tools use boot flag to assign a very long GUID to the ESP - efi system partition. It really is required.
 UEFI boots from that partition which must be inside the first 2TiB of a drive (usually not an issue, but UEFI suggests it be first or near beginning of drive) and partition must be FAT32.

UEFI can boot from MBR partitioned drive, but UEFI recommends full installs use gpt. Installers, if both BIOS & UEFI often use MBR partitioning and some older UEFI/BIOS wanted either MBR or gpt and did not work with the other. Windows full install only boots from gpt partitioned drives in UEFI boot mode.

---

### Post by norbertk237 on 2019-05-18
I have partitioned the usb using gpt and now I also set the boot flag, it still doesn't start up, the same message appears.

---

### Post by oldfred on 2019-05-18
Is flash drive FAT32, with boot flag to make it the ESP & do you have /EFI/Boot/bootx64.efi in ESP - efi system partition.

---

### Post by norbertk237 on 2019-05-19
Yes, I have a single FAT32 partition, I created a guid partition table and also set the boot flag. Before switching the boot flag, I was able to open the flash drive in Files and I did see /EFI/boot/bootx64.efi (as far as I remmber, it was lowercase boot), after turning on the boot flag, I cannot mount the driver any more. Also, the esp flag was turned on automatically when I selected boot.

---

### Post by oldfred on 2019-05-19
Whether you have boot flag on or not, you should be able to see files in a FAT32 partition.
And with FAT32 or NTFS case does not matter. In fact if from Linux you create both Boot & boot (files or folders) Windows then will not work as it just sees two identical folders and that is not allowed. 
If you cannot read the flash drive, then UEFI cannot read it.

---

