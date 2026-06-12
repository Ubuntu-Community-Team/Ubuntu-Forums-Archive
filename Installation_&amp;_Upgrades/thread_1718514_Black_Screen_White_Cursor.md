---
title: "Black Screen White Cursor"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by Brixton on 2011-03-31
I've installed Ubuntu to an internal harddrive which was wiped and in RAW format before installation. It is not a dual boot, and I tell my motherboard to boot that drive as the primary drive, in hopes of having a clean Linux install. The machine is normally a Windows machine, but I wanted to hot swap OSes using different HDDs. The motherboard is an Asus P6T Deluxe V2, the graphics card is Nvidia GTX275, and it's a 32 bit version of 10.10.

I never see the GRUB menu, a BIOS error, or any text beyond my motherboards boot sequence text. The only thing I see is a black screen with a white cursor, the actual HDD contains the Linux system.

The tried two verified Ubuntu CDs and a flashdrive. I always wipe the drive to RAW before I try again.


 I have installed dual boots, single boots, the works to a lot other boxes, but this is my first attempt on this config.


Edit: The problem is with the installer itself, it seems randomly the secondary drives were getting the bootloader installed even when the "use entire disk" option was used. Thanks for your help Rubi1200, I've saved your info incase I do this again.

---

### Post by Rubi1200 on 2011-03-31
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

