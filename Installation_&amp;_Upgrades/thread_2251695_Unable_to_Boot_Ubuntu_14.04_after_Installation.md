---
title: "Unable to Boot Ubuntu 14.04 after Installation"
date: 2014-11-06
forum: Installation &amp; Upgrades
---

### Post by 10106944 on 2014-11-06
I installed Ubuntu 14.04 to replace my Windows 8 operating system. I did this via usb.
It seemed successful, but for some reason won't boot. Instead, I am offered the options to either 1) Install Ubuntu or 2) Try Ubuntu.
Before anyone suggests it, I know I am booting from the hard drive and not from the usb - I have already changed the boot order correctly.
When I try to reinstall, it says Ubuntu 14.04 is already installed as the operating system, and asks if I want to partition.
Other than that, I ran boot-repair, and was given this boot info: [http://paste.ubuntu.com/8839181/](http://paste.ubuntu.com/8839181/)

I'm new to Ubuntu so any help would be greatly appreciated!

---

### Post by Bucky Ball on 2014-11-06
*Thread moved to **Installation & Upgrades**.*

As you're new here, we'll be gentle (won't we?), and you have a better chance of support here. ;)

Welcome. So you ran recommended repair in Boot Repair, it didn't work? The install USB is unplugged from the machine when you cold boot (switch it off, remove all USB dongles and boot)?

---

### Post by 10106944 on 2014-11-06
Thanks for the welcome! Okay I unplugged the USB and now when I boot the computer it just says "Insert system disk in drive." :|

---

### Post by Bucky Ball on 2014-11-06
So it is booting from the USB. I'd perhaps recheck the BIOS and leave the dongle out from now on and work out why it's not booting. Perhaps burn a Boot Repair USB or disk and boot from that and run it again. 

Your bootinfo tells us you have Ubuntu and a /swap installed and everything looks aok.

Just another point: you don't need to use EFI. If you've only just begun you could scrap that and reinstall in regular BIOS mode. (CSM from memory).

---

### Post by oldfred on 2014-11-06
You show this:
BootOrder: 0002,0000,0001 
Boot0000* USB Memory 
Boot0001* HDD/SSD 
Boot0002* ubuntu.

So Ubuntu is installed and listed by UEFI.

What brand, model computer?
Some will only boot Windows by name and we have to have work arounds.

Since only Ubuntu installed you can rename it to be Windows in UEFI and then UEFI thinks it is booting Windows.
You have to boot live installer in UEFI boot mode to have efibootmgr.

 # from liveDVD or flash booted in UEFI mode and use efibootmgr, this is what Boot-Repair reported:
modprobe efivars
sudo efibootmgr -v

This can be either grub or shim:
  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

      [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Other work arounds:
      [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019
[/URL]Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)


 Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

    [URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

### Post by 10106944 on 2014-11-07
It's a Toshiba Satellite U920T.
I typed [FONT=courier new]sudo efibootmgr -v[/FONT] and it said [FONT=courier new]command not found[/FONT].
Would that cause a problem? Should I install efibootmgr? Then, I assume, change the description to Windows?

---

### Post by 10106944 on 2014-11-07
I can't change the BIOS mode to CSM, it's on UEFI and doesn't give me an option to change.

---

### Post by oldfred on 2014-11-07
You installed in UEFI mode, so you want UEFI mode.

Do you have secure boot on? Usually better for now with it off, but still in UEFI boot mode.
CSM mode is not available or does not have a secure boot mode.

You have to boot Ubuntu installer in UEFI mode to have efibootmgr work. 
I thought it was installed by default, but it will not work if in BIOS boot mode.

---

### Post by 10106944 on 2014-12-10
Secure boot is off, and this is the result I get from sudo efibootmgr -v
```
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0002,0003,0001,0000
Boot0000* USB Memory    ACPI(a0341d0,0)PCI(14,0)USB(0,0)
Boot0001* HDD/SSD    ACPI(a0341d0,0)PCI(1f,2)ATAPI(0,0,0)
Boot0002* ubuntu    HD(1,800,100000,f35087f8-0cc1-4b86-afe6-2f9fce94578c)File(\EFI\ubuntu\shimx64.efi)
Boot0003* Windows Boot Manager    HD(1,800,100000,f35087f8-0cc1-4b86-afe6-2f9fce94578c)File(\EFI\ubuntu\shimx64.efi)

```

What do I do next?

---

### Post by oldfred on 2014-12-10
If in your UEFI menu you now choose to boot "Windows" which now is really the same shim as the ubuntu entry, does it boot? And can you set that as the default?
The vendors hard code the UEFI to only allow the default boot to be the "Windows" entry, but so far they do not check that it really is booting Windows.

---

