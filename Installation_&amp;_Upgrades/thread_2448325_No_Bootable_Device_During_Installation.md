---
title: "No Bootable Device During Installation"
date: 2020-08-05
forum: Installation &amp; Upgrades
---

### Post by vickia on 2020-08-05
I am trying to install a clean Linux (single boot) on a Dell Inspiron 11-3162. The BIOS is American Megatrends Aptio Setup Utility 2.4.0

I have made a USB setup file using Ubuntu and Etcher. However, whenever I get the USB selected in the BIOS, and the system checks the USB,  the system says there is no bootable device.

There are some options under the BIOS boot page under UEFI that are confusing. 

Fast Boot
Add Boot Option
Delete Boot option
Secure Boot
Load Legacy Option Rom

When I select "add boot option" I get a screen that says "select media drivers". They all start with Acpi, They mention PCI 10|0 or 14|0, Pat1, and Sig with a string of 8 characters. If I select either of the first two, I then have the opption to select <EFI>. The third driver gives me a number of options including:
<system volume information>
<boot>
<EFI>
<sources>
<bootmgr>
BOOTNXT
dbx
db
KEK
PK

I am then able to select one option, name the file, and set that file in the BIOS as the one to boot with. I have been assuming "bootmgr" is the one I want, but no luck so far.

I deleted the Windows boot manager as I have no intention of reinstalling Windows. However, the number of media devices has increased from one to three after multiple attempts to get this going. 

I have tried just about every combination of these, and I can't get it to work. I have also enabled and disabled UEFI, tried booting using "legacy", turned on and off "secure boot", and many more.  Also, I tried an installation of Linux Mint and different USB stick, and got the same thing.

I have done these installations on other laptops with no problems.

Any help would be appreciated.

Thank You.
VA

---

### Post by oldfred on 2020-08-05
I have not seen anyone add a boot option via UEFI menu.
Normally grub install will add its entry as part of the install.
Or a reinstall of grub will also add it.

But you need gpt partitioning and an ESP - efi system partition and have installed in UEFI boot mode.
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You can also add entries to UEFI with efibootmgr. Just about everyone but HP supports that. HP seems to erase those entries on reboot. And it may be Windows syncing BCD with HP's UEFI.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by vickia on 2020-08-05
> **oldfred said:**
> I have not seen anyone add a boot option via UEFI menu.

But you need gpt partitioning and an ESP - efi system partition and have installed in UEFI boot mode.
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Oldfred,
Thank you!! I was able to glean enough information from that link to get it going.
Vickie

---

### Post by pbear42 on 2020-08-06
> **vickia said:**
> I have been assuming "bootmgr" is the one I want, but no luck so far.
Sounds like you've solved the problem (congratulations!), but for future reference, that's the name of the *Windows* boot manager.  So, no, never was what you wanted here.

---

### Post by vickia on 2020-08-06
Once I understood that I had to have the USB stick inserted in order to select the correct media file (and then the correct Linux boot manager - Grub whatever) to set up the BIOS, things went smoothly. That was why I mentioned in the original post that the number of media devices kept "changing"...it took a while to make the mental connection that it had to know which file from the USB stick would set it up properly :) ... duh -- how else could it know?

Once I read through the link you sent, something "clicked"...

Again, thank you!

Vickie

---

