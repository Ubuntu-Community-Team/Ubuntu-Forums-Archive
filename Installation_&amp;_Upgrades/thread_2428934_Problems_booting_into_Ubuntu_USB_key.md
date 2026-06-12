---
title: "Problems booting into Ubuntu USB key"
date: 2019-10-11
forum: Installation &amp; Upgrades
---

### Post by aphandersen on 2019-10-11
I have an old Acer Aspire E14 with Windows 10 - and of course Windows 10 is broken, I cannot access this and cannot reinstall. I have decided to remove Windows 10 and only run Ubuntu on the machine. I have already formatted the hard drive. 

Then I have made an USB key with Ubuntu from Linux Mint (which I have on another computer) using UNetBootin. On my Acer machine I have made USB boot 1. priority. When I start the machine with the USB key, it comes into the GRUB boot menu where I can select to install Ubuntu or try Ubuntu. But no matter what I choose I get the following mistake. 

error: /casper/vmlinuz has invalid signature
error: you need to load the kernel first. 
Press any key to continue

When I press a key I come back to the menu again. 

I have tried to disable Security Boot in BIOS. When I do that I still get into the GRUB Boot menu, but now it shows the following mistake:

error: invalid magic number
error: you need to load the kernel first. 
Press any key to continue

I have also tried to disable UEFI boot completely, but then it cannot start the GRUB bootmenu. 

Any ideas to how I can get Ubuntu installed?

---

### Post by guiverc on 2019-10-11
It sounds like either your download was faulty (did you md5sum or validate your ISO?  [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)) or the write to media failed (there is a 'check disc for defects' option for this ([https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)), but I suspect your thumb-drive-image is too badly damaged to use this; it's better at detecting minor flaws not major ones).

I'd verify your ISO that was written, if it passes, I'd write another to thumb.drive.  If it has the same issue, I'd use another box to verify image and if it passes - you know it's something specific to the box you want to install on...

---

### Post by dfault2 on 2019-10-11
Use Rufus or Etcher for creating the bootable usb stick. Works without any problem

---

### Post by oldfred on 2019-10-11
Some of the tools to create bootable USB flash drive, specify UEFI or BIOS boot of flash drive. Then you have to select correct/same boot mode when booting flash drive. Most systems with UEFI Secure boot off will show two entries for booting USB flash drive. One UEFI:flash and other flash where flash is name or label of flash drive. Mine says PMAP.

You may want UEFI Secure Boot off, but to set "trust" on UEFI boot entry after install will need UEFI password (never lose that or reset when done) to set trust. You may need password  for other settings in UEFI also.
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by aphandersen on 2019-10-11
Thank you all for help until now. I bought a new USB key and used the Ubuntu Start disk creator tool to create a live USB key. This works, so I now can open up live Ubuntu running from the USB key. 

However I have a new problem, when I try to install Ubuntu using this USB key. When I install I cannot see the hard drive where Windows used to be installed (and using Windows command prompt been formated). I can only see the space on the USB key. 

I cannot see the harddrive either in the install program, in GParted or in the tool Disks. 

Some ideas or reasons why it does not show up?

---

### Post by oldfred on 2019-10-11
Is setting in UEFI for drives set to AHCI?

Or if left over NTFS partitions with hibernation flag from fast start up in Windows.

Have you updated UEFI to latest version. Some older Acer UEFI did not work correctly. If SSD also update SSD firmware.

Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

