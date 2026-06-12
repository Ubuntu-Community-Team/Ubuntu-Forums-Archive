---
title: "Boot-repair paste-bin"
date: 2019-04-19
forum: Installation &amp; Upgrades
---

### Post by aitchsee on 2019-04-19
Hello. Trying to set up Ubuntu on a Toshiba click 10. I deleted Windows and formatted drive installed Ubuntu from flash drive but it wouldn’t boot. Tried Boot-Repair & it says it’s fixed but it still won’t boot. Here is the paste-bin [http://paste.ubuntu.com/p/whbYTV56xG/](http://paste.ubuntu.com/p/whbYTV56xG/)
Thank you &#128522;

---

### Post by TheFu on 2019-04-20
Support for Ubuntu 14.04 ends THIS MONTH.  Best not to both installing or troubleshooting that version.
18.04 is the current LTS supported until 2023.
16.04 is the prior LTS supported until 2021.

Sometimes a BIOS doesn't follow UEFI standards, so manual intervention is necessary.  On an old 2015 toshiba chromebook, I had to rename a file for the BIOS to boot it. I don't recall the name and since it was a different model than yours, it might be different.  On my current system, not a toshiba, files in /boot/efi/EFI/ubuntu/ are 
./fwupx64.efi
./grubx64.efi
./grub.cfg
./shimx64.efi
./mmx64.efi

Newer versions of the Ubuntu installer probably handle some of these situations better.  Someone else will probably be along soon with lots-o-links on the issue.

---

### Post by yancek on 2019-04-20
Have you made the change in the BIOS suggested in the boot repair output?

> Please do not forget to make your BIOS boot on mmcblk0p1/EFI/ubuntu/shimx64.efi file!

An explanation of "wouldn't boot" would be helpful.  More details on what exactly happens.

---

### Post by aitchsee on 2019-04-20
Thank you. I did download install 18.04 first of all (boot errors there too) but then it failed to open on the live usb so I back-tracked. I&#8217;ll try 18.04 again. Thanks for the tip about renaming files - I&#8217;ll have a go at that

---

### Post by aitchsee on 2019-04-20
> **yancek said:**
> Have you made the change in the BIOS suggested in the boot repair output?



An explanation of "wouldn't boot" would be helpful.  More details on what exactly happens.


Sorry for scant details. On boot I get the error message:
Failed to open \EFI\BOOT\grubx64.efi :Not Found
Failed to load image \EFI\BOOT\grubx64.efi :Not Found
start_image() returned Not Found 

I can’t find a way to alter how the machine looks for the designated directories (I only have two keys to enter BIOS - F12 brings up a boot menu but there seems to be no way to change boot order, I just have to select the USB each time, and F2 brings up what Toshiba call a set-up menu and the only useful option is to select secure boot or disable. I’ve tried both but I get the message above with both.

Thank you

---

### Post by TheFu on 2019-04-20
Well, you know the name of the file and where it is looking for it.  
Next step is to ensure that the boot file is in that location.

Also, be certain to use the "Try Ubuntu" option before the install. See that everything is working and make a list of what doesn't since you'll want to research those to see if anyone else got them working or not.  For example, my laptop has a fingerprint reader that will never work because there isn't any driver for it. I'm not a big fan of using body parts for passwords, seems like a bad idea to encourage someone to cut my finger off to access my super-secret recipes.

---

### Post by oldfred on 2019-04-20
Does not f12 show these entries? 

```
        BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0001,0000,2001,2002,2003
Boot0000* Windows Boot Manager	HD(1,800,100000,08c78291-30a1-4bbe-8c63-43f88f1e45e4)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0001* ubuntu	HD(1,800,100000,08c78291-30a1-4bbe-8c63-43f88f1e45e4)File(EFIubuntushimx64.efi)
Boot0002* EFI USB Device (SanDisk)	ACPI(a0341d0,0)PCI(14,0)USB(2,0)USB(0,0)HD(1,800,3947800,002d3b68)RC 
    
```

And shimx64.efi should then boot as that is the shim for Secure boot but works with Secure boot off.
And system should be booting /EFI/ubuntu not the hard drive entry /EFI/Boot.

---

