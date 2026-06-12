---
title: "Ubuntu froze during install, and now BIOS won't boot."
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by kris2 on 2013-08-01
Okay so, major problems. I've been attempting to install Ubuntu 12.04 64 bit onto a Toshiba Satellite C855 laptop with stock Windows 8 and, after changing around my BIOS settings, had the install running from a USB flash drive. When the installation was nearing completion, while I was away from the computer, the system froze. With no other option, I did a hard reboot. The problem is that after it rebooted, it brought me to a black screen with no BIOS or any other kind of options. I tried booting the USB again; nothing. Tried reloading Ubuntu onto the USB drive; still nothing. Tried booting from a disk and still no luck. Next, I'm planning on trying to boot Windows 7 from USB but am not too confident I'll have any success. I tried doing a factory reset, and there was still no response. All I have is a black screen with a blinking underscore with no ability to input any kind of commands. I'm worried it may be done for. I don't really know that much about Windows or Ubuntu, so maybe I'm missing something?

---

### Post by oldfred on 2013-08-01
Did you turn off fast boot in Windows? Back up the efi partition and Windows? 
Can you still get into UEFI/BIOS and choose to boot either Windows or ubuntu?

If an Ultrabook, you may also have RAID issues from Intel SRT which prevents grub from correctly installing and video issues from the dual video. Can from UEFI you set to boot one video mode or the other.

See also link in my signature.

---

### Post by ubfan1 on 2013-08-02
[LIST=1]
[*]Ensure your firmware is at least 6.60 (6.70 was just released, but the release notes didn't say much except a W7->W8 upgrade fix.).
[*]My Satellite S855 has just the Intel video HD4000, and just a regular hard disk, and there were no issues with installing with secure boot on.
[*]Grub won't boot Windows even after fixing the chainloader command, so I use the EFI device selection to select hard disk, then Windows to get into Windows (all with secure boot on).  If you ever run boot-repair, do not let it rename the bootloaders, that's unnecessary, and will probably break the efi boot to windows, running you back through grub.
[*]Second install, (first to HD), my /EFI/ubuntu directory was corrupted, and I had to do a manual repair (bug 1090829?).  If you can successfully read the EFI files, back them up.
[*]Booting off a usb with an EFI partition on it with a /EFI/Boot/bootx64.efi which is a copy of shim.efi and grub64x.efi (signed) present in /EFI/Boot, and grub.cfg in /EFI/ubuntu should work, and is a good emergency boot mechanism.  You can set up the grub.cfg to actually run the Ubuntu installation off the hard disk.  Keeping such a setup in /EFI/Boot on the hard disk gives you a fallback boot mechanism when the selected hard disk efi selection fails (like when the Ubuntu selection is for ...grubx64.efi, which cannot boot with secure boot (should have been shim but something in the installer can fail and put the wrong one into the efi menu).
[*]You can explicitly add a correct efi menu item (to shim) with the grub-install --uefi-secure-boot  (? check the switch). I'd leave any incorrect grubx64 entries alone, since the correct entry on my 13.04 machine got deleted when I updated a 12.10 USB stick!  (Should file a bug).
[*]All the factory defaults for boot speed=normal and windows faststartup=not checked were correct for installing Ubuntu, just had to change the boot order to make usb and dvd before the hdd.
[/LIST]

---

### Post by oldfred on 2013-08-02
Boot-Repair has just changed how it renames. It does not rename Windows file unless you specifically request it. Some computers have modified UEFI to only boot the Windows efi file and then the rename is required.

 This option now under advanced choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)

---

