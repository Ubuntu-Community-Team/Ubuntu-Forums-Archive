---
title: "Windows does not start in dual mode"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by bertverhees on 2013-03-07
error message:
/EndEndtire
file path: /APCI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD/(2,e1800,82000,cc51b24f9affe111,a6,eb)/File(\EFI\Boot)/File(bkpbootx64.efi)/Endtire
error: cannot load image

the URL is:
[http://paste.ubuntu.com/5592604/](http://paste.ubuntu.com/5592604/)

Thanks very much for support

kind regards
Bert Verhees

---

### Post by oldfred on 2013-03-07
Did Boot Repair create this file before as it is not there now.
bkpbootx64.efi

Boot-Repair will name and un-rename Windows files for some UEFI that only boot Windows files.
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

But UEFI often remembers boot entries until you manually edit out entries in UEFI. I used to think it scanned efi partition to find boot files, but it actually saves that info in its own memory and reuses it.

---

### Post by bertverhees on 2013-03-07
Thanks, just disabling SecureBoot sovled the problem

kind regards
Bert Verhees

---

