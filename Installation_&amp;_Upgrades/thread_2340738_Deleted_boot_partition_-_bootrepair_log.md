---
title: "Deleted boot partition - bootrepair log"
date: 2016-10-21
forum: Installation &amp; Upgrades
---

### Post by josescxavier-q on 2016-10-21
Hello,

I have deleted my boot partition acidentally :( After some research I have installed boot-repair on a live cd but it give me one of the following errors:

Boot-repair: > The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?

[IMG]http://i.imgur.com/swbMN13.png[/IMG]

Select YES and here is the result pastebin:  [http://paste2.org/VbpMk0Uz](http://paste2.org/VbpMk0Uz)

after run boot-repair the gparted looks the same and boot still doesn't work :(

---

### Post by oldfred on 2016-10-21
You have UEFI hardware.
You have what looks like mostly an UEFI install of Ubuntu, but have grub installed to gpt's protective MBR for BIOS boot, but no bios_grub partition which is required for BIOS boot.
But in fstab the mount of the ESP - efi system partition is commented out (probably from BIOS install of grub?).

I would boot installer in UEFI mode, and run Boot-Repair's advanced mode to run a full un-install/reinstall of grub2. That will remove the BIOS grub install and install the UEFI boot. It will not erase the MBR, but since not ever used it will not matter. Just do not try to boot in BIOS mode from UEFI as that will not work.
Always boot in UEFI mode from UEFI/BIOS.

---

### Post by josescxavier-q on 2016-10-21
> **oldfred said:**
> You have UEFI hardware.
You have what looks like mostly an UEFI install of Ubuntu, but have grub installed to gpt's protective MBR for BIOS boot, but no bios_grub partition which is required for BIOS boot.
But in fstab the mount of the ESP - efi system partition is commented out (probably from BIOS install of grub?).

I would boot installer in UEFI mode, and run Boot-Repair's advanced mode to run a full un-install/reinstall of grub2. That will remove the BIOS grub install and install the UEFI boot. It will not erase the MBR, but since not ever used it will not matter. Just do not try to boot in BIOS mode from UEFI as that will not work.
Always boot in UEFI mode from UEFI/BIOS.

But should I create the partition or not on gparted?

---

### Post by oldfred on 2016-10-21
Not unless you really want BIOS boot.

Then you have to create a 1 or 2MB unformatted partition with the bios_grub flag. It can be anywhere on drive.
Then when you reinstall a BIOS version of grub it should work if you boot from UEFI in BIOS/CSM/Legacy mode.

For all my drives & larger flash drives I put both the ESP & bios_grub on every drive. And usually now boot in UEFI mode, but can easily reconfigure for BIOS if need be.

---

### Post by josescxavier-q on 2016-10-22
> **oldfred said:**
> Not unless you really want BIOS boot.

Then you have to create a 1 or 2MB unformatted partition with the bios_grub flag. It can be anywhere on drive.
Then when you reinstall a BIOS version of grub it should work if you boot from UEFI in BIOS/CSM/Legacy mode.

For all my drives & larger flash drives I put both the ESP & bios_grub on every drive. And usually now boot in UEFI mode, but can easily reconfigure for BIOS if need be.
I just want to be able to boot my pc right now :s

When I run boot repair it says that I should have a partition like I said on the first post. BTW I'm running the live usb in UEFI mode.

So, I should delete the /dev/sda1 and run boot-repair?

---

### Post by oldfred on 2016-10-22
No need to delete sda1. Like I said, I keep both the ESP & bios_grub on all drives.

But if you have updated grub using advanced mode full reinstall, from Boot-Repair in UEFI mode, you must make sure you have set UEFI/BIOS to boot in UEFI mode, not BIOS/CSM/Legacy. And often better to have Secure boot off, many call it "Windows" or "Other".

---

