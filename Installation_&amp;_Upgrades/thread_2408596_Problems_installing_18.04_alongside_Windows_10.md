---
title: "Problems installing 18.04 alongside Windows 10"
date: 2018-12-20
forum: Installation &amp; Upgrades
---

### Post by danielsg94 on 2018-12-20
Hey reader,

I actually already installed ubuntu once, but it only works when I set the bios to legacy mode.
Now when the bios was in legacy mode, ubuntu would boot.
If the bios was set for both or uefi alone, it starts Windows. 
Grub was also missing.
I've read that there might be a problem with my bios. Can you tell me something on that?
I cleared the partitions with ubuntu again.
Trying to launch ubuntu from usb in uefi, ends in a dark screen, but nothing happens. 

Thank you very much
Dan

---

### Post by yancek on 2018-12-20
Start by reading the Ubuntu documentation at the link below.  From the info you posted, you apparently installed Ubuntu in Legacy/CSM mode while windows was UEFI.  In that case, the Ubuntu Grub bootloader will not boot a windows EFI install.  Both EFI is necessary.  Disable Legacy/CSM in BIOS before booting the Ubuntu media.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by danielsg94 on 2018-12-20
I tried just that, however now when press F12 and tell it to boot from USB, it doesn't do it. The PC simply reboots.

EDIT: SOLVED. I used the wrong datatype while moving Ubuntu to the usb.

---

