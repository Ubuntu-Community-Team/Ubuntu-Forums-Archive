---
title: "Installation doesn't detect existing efi partition"
date: 2023-10-13
forum: Installation &amp; Upgrades
---

### Post by Onesimus on 2023-10-13
I currently have Ubuntu 22.04.3 installed on my PC.  It boots in UEFI mode (I set up a /boot/efi partition to allow this to happen)

I am wanting to install 23.10 over it.  However, the installation doesn't detect this partition as bootable.  
Hence the only boot loader option available is the USB drive that has the installation files on.

I am expecting that the boot loader should be installed on the hard disk that Ubuntu 23.10 is on.

Any thoughts ?

---

### Post by sudodus on 2023-10-13
I understand that you boot in UEFI mode.

Do you want to overwrite the whole drive or do you want to keep/reuse part of it?

[hr][/hr]
- If you want to overwrite the whole drive, it should be straightforward.

The Ubuntu installer should be able to create a fresh partition table including everything necessary.

If still problems, boot into the live USB drive and run gparted to create a fresh GUID partition table, GPT. You need not create any partitions.

Then try again with the Ubuntu installer and let it use the whole drive.

[hr][/hr]
- If you want to keep part of what is on the drive now, please describe with details what you have and what you want.

---

### Post by Onesimus on 2023-10-13
I have a number of existing partitions (40Gb for /  ;   200Gb for /home  ;  and the /boot/efi).
I want to replace the current installation (22.04.3) with the new installation on the 40Gb partition, but want to keep the 200Gb partition as there it is where all my documents, etc are).

The installer detects the 700Mb partition (formatted at vfat), but won't allow me to set it to /boot/efi  (despite that fact that this partition is used for the current installation)

I am assuming because the installer doesn't see that partition as bootable, then it won't give me the option of setting it as the boot loader

(In addition, the installer won't allow me to select a partition to be formatted.  There is a check box next to the partition but selecting it makes no difference).

---

### Post by sudodus on 2023-10-13
From your join date I conclude that you know the old Ubuntu installer, Ubiquity, well. You can actually use it instead of the new one, if you download the 'legacy iso file'

**[FONT=Courier New]ubuntu-23.10-desktop-legacy-amd64.iso[/FONT]**

from [cdimage.ubuntu.com/ubuntu/releases/23.10/release/](http://cdimage.ubuntu.com/ubuntu/releases/23.10/release/)

where you also find the sha256sum.

---

### Post by Onesimus on 2023-10-13
Many thanks, I will give that a try.

---

### Post by MAFoElffen on 2023-10-13
Since you say that the Installer would not recognize your EFI partition... The first thing I would suggest for your computer is to first verify that it (indeed) booted in UEFI mode from the Installer LiveUSB = Check for the existence of /sys/firmware/efi/efivar/ and that that folder it is populated.
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"

```

---

### Post by ubfan1 on 2023-10-13
The new subiquity installer in Ubuntu 23.04 Fixed the bug 1396379 -- Grub put on wrong disk, but not the way you'd expect. A 1GB EFI partition gets made if a valid one is not detected on the target device.  The "something else" manual screen does not allow the creation of an EFI sized to your needs, doesn't even allow the initial creation of a FAT partition (but you can edit an existing one and make a FAT fs). It should have accepted your EFI created before the install if it completely valid -- FAT, esp flag, boot flag.  The old installer should work for you since you have only one disk.

---

