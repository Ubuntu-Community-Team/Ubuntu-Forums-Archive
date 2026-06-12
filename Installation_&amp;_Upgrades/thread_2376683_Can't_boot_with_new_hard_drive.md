---
title: "Can't boot with new hard drive"
date: 2017-11-04
forum: Installation &amp; Upgrades
---

### Post by hyjack2 on 2017-11-04
I recently built a new PC and for a hard drive I thought to use Ubuntu. I don't have access to a secondary computer so I'm using my mobile device to download and transfer files.

The problem is that my computer isn't registering it as something it can boot from, so please tell me what I'm doing wrong.

This is my process:
 - Download Ubuntu 17.10 on to phone
- Transfer file into SanDisk 32GB USB
- Plug USB into computer
- Change boot priority to USB

Then I get the message "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key" which repeats every time I press a key.

Can someone tell me what I'm doing wrong please?

---

### Post by monkeybrain20122 on 2017-11-04
You have to "burn" the iso into the usb to create a bootable usb. Simply putting the iso there doesn't work. I don't know what to tell you if you don't have another computer available to create the bootable usb,

---

### Post by oldfred on 2017-11-05
If a new computer, it is UEFI.
But do not know of a way from a phone to extract ISO. Only if you have grub already installed to flash drive and can edit grub.cfg to loopmount can you directly boot an ISO.

       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

