---
title: "Ubuntu 13.04 live cd won't boot"
date: 2013-06-21
forum: Installation &amp; Upgrades
---

### Post by Genxi on 2013-06-21
Hi guys,

I am trying to dual boot ubuntu with windows 8 using the guide from this link: 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

However, When I get to the grub page to "try ubuntu" it doesn't boot at all, same goes with the capability mode.

I have secure boot, fastboot and fast startup disable as per the directions. Bios is in uefi mode.

Any ideas?


Thanks.

---

### Post by low_rider on 2013-06-21
What did you store the live cd on? Was it an actual disk or was it a usb stick?

---

### Post by Genxi on 2013-06-21
It was on an actual dvd disk, yes. When I choose the option "try ubuntu" it goes to a black screen and hangs.

Edit: The dvd booted fine into live cd mode on my old laptop with uefi.

---

### Post by Bashing-om on 2013-06-21
[COLOR=#000000]Genxi; Hi !

Perhaps a graphics driver issue... try booting:
From cold start, when bios screen clears depress and hold shift key -> language screen, escape key to accept the default -> boot options screen;
f6 key for the preset options -> arrow to the "nomodeset" option space or escape key to accept and the enter key to continue the boot process. 

If this works, further advise pending for the actual install.
[/COLOR][INDENT=3][COLOR=#000000]
hope this helps

[/COLOR][/INDENT]

---

### Post by fantab on 2013-06-22
[s]If you have a pre-installed Windows8 then disable 'Fast Startup' and 'Fast/Quick Boot'. Fast Boot can be disabled from BIOS/UEFI. 
Fast startup can be disabled from within Windows8: [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)[/s]

Edit: didn't read your post fully. 

If you have an SSD pre-installed then check in the BIOS for 'Intel SRT' and disable it. While you are in BIOS see what mode is SATA set to, it should be AHCI.

---

### Post by oldfred on 2013-06-22
If bootining in UEFI mode you do not get the accessibility icons and the typical BIOS screens. You just get grub menu like after an install.

But you still may need the nomodeset boot parameter depending on your video.

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS live installer Boot Options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:

press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

---

