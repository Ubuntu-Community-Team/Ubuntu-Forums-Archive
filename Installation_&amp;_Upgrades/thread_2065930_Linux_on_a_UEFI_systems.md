---
title: "Linux on a UEFI systems"
date: 2012-10-03
forum: Installation &amp; Upgrades
---

### Post by jpaulb on 2012-10-03
I ran across an article called "***[SIZE=2]Configuring Linux to run on UEFI based systems where GRUB fails to install [/SIZE]***

"
[http://goo.gl/RR1Rp](http://goo.gl/RR1Rp)
 Is this a Linux or a GRUB issue?
Will it be resolved in 12,10?

---

### Post by drmrgd on 2012-10-03
It's really neither.  12.04 runs perfectly well with UEFI BIOS.  However, it needs to be set up and configured a little differently than BIOS MBR does, which may be why that poster had problems.  A couple things that need to be done:

1.  The 64-bit version of Ubuntu comes with the EFI Grub version.  I believe that 32-bit can be built, but is not EFI compatible out of the box.

2.  The installer device (USB, CD, DVD, etc.) must be booted in UEFI mode and not in standard BIOS mode.  For my ASUS board, there was an option for either, and I found that if I didn't explicitly choose to boot the USB in EFI mode, the EFI Grub bootloader was not installed by default.

3.  The drive should be GPT formatted with an EFI_boot partition where the EFI Grub will reside.  If dual booting, this should be the primary boot device.

There's some more documentation on how to set this up, as well as the very excellent Boot Repair tool that will help fix any configuration issues or whatever:

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

In short quite a few people have gotten stable UEFI dual boot systems up and running without too much difficulty once they've configured things appropriately.  Also, if you decide to try it for yourself, there are a number of users here who are experts at setting this up and can help with any problems.

---

### Post by pompel9 on 2012-10-03
When I got my UEFI motherboard, I didn't have any troubles.

I had to boot into safe mode and install the graphics driver. But that was all. The motherboard automatically choose UEFI mode for my SSD disk.

---

### Post by YannBuntu on 2012-10-04
> **jpaulb said:**
> I ran across an article called "***[SIZE=2]Configuring Linux to run on UEFI based systems where GRUB fails to install [/SIZE]***

"
[http://goo.gl/RR1Rp](http://goo.gl/RR1Rp)

This article gives incorrect advice.


> **jpaulb said:**
> Is this a Linux or a GRUB issue?
Will it be resolved in 12,10?

Mainly GRUB and Ubiquity (the Ubuntu installer) issues.
But most issues can be solved easily if you install 12.04.1-**64bit** then use Boot-Repair.
See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Some issues are still not solved in 12.10, so Boot-Repair will still be necessary.

---

### Post by jpaulb on 2012-10-05
Thanks. The reason I asked was I want to buy a laptop and have it dual boot. 
I just do not wish to play around with any more M$ induced problems than necessary.

---

