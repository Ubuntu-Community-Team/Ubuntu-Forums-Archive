---
title: "Ubuntu 12.04 dual boot with Windows 8"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by Chackal on 2012-06-22
Hi everybody

I am trying to help a friend of mine with this issue... His main OS right now is Windows 8 (believe it or not :mad:) 64 bits and we are trying to dual-boot with Ubuntu 12.04 32 bits.

The Ubuntu installation itself does not recognize Windows 8 installed on the hard drive, so we have to manually edit the partitions... We are not sure about how to configure the boot settings, and no matter which combinations we try we always get straight to Windows 8 when restarting.

Any advice concerning this? Did someone succesfully do this dual-boot thing with only Windows 8 and Ubuntu? The only cases that I can find are triple-boot (7, 8 and Ubuntu) and/or Windows and Ubuntu in different hard drives.

His machine is [this one]("http://www.ebay.de/itm/Gamer-PC-Intel-Core-i7-2600K-16GB-DDR3-GTX-560-USB3-0-/160635197093?pt=DE_Technik_Computer_Peripherieger%C3%A4te_PC_Systeme&hash=item25669a96a5").

Thanks in advance

---

### Post by westie457 on 2012-06-22
Hi had Windows 8 dual-booting a while ago. Had to do it this way if my memory is working correctly.

Install Windows 7 then install Ubuntu.

Upgrade to Windows 8 then use a LiveCD in 'try' mode and run ```
sudo update-grub
``` in a terminal.

Never tried Windows 8 as a clean install. Also have got rid of it as it did not play nicely with my hardware which is nowhere as well specc'ed as what your friend has.

Hope this helps.

---

### Post by oldfred on 2012-06-22
Is Windows installed in UEFI with gpt partitions or BIOS with MBR partitions? Motherboards with i7 have the new UEFI, but not the proposed locked down Windows 8 version.

You have to install Ubuntu in the same mode. Both Windows and Ubuntu should have two choices from a UEFI system, either new UEFI or legacy/BIOS or whatever they call the old way.

If first partition is efi and using gpt partitions then you are in UEFI/efi mode.

Also:
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

