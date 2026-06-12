---
title: "Help dual booting windows 8 with Ubuntu 12.04"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by blackadam on 2013-04-18
I just got a new laptop (Acer Aspire E1-571-6680) with windows 8 64bit.  i have been trying to dual boot it with ubuntu 12.04 off of a usb drive with no luck.  i'll go into the bios and changed to order to boot from usb first that didn't work.  it would go straight to windows.  i rearranged the whole boot order and used all the possible usb choices to boot before the windows boot loader but niet goes straight to windows.  how could i if possible dual boot it??

---

### Post by ubfan1 on 2013-04-18
Are you using the 12.04.2 64 bit version of Ubuntu?  That is the only one which should boot on a "secure boot" enabled machine, which all W8 preinstalled machines are.

---

### Post by oldfred on 2013-04-18
You also have to have second drive partitioned as gpt, really should have efi partition first as required by UEFI, but grub will probably be installed to the efi partition on the Windows drive.

Others who have done similar installs to second drives.
       Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

