---
title: "Installation on External USB HDD"
date: 2013-07-20
forum: Installation &amp; Upgrades
---

### Post by junweixiong on 2013-07-20
Hey guys!

I am trying to install Ubuntu 12.04 on a external HDD for my MacBook Air (128GB). I know some topics about this may be out there, but they don't answer my question.

So, I downloaded the .iso and created a Live USB on my thumb drive, and from there, I tried to install Ubuntu to my external HDD.

Here's what I did:

Created a new partition table.
Created / partition
Created /home partition
Created swap partition
Created /boot partition (just to make sure)
Created efi partition
Created grub partition (for my Windows computers)

However, when I tried to boot, it does not come out on the EFI boot selection menu. Only my internal OS X partition is listed.

Anyone successfully installed Ubuntu on a external HDD and booted it on a EFI/UEFI computer? Share your experiences. All help is appreciated. I want to use Linux for my Android development, and I hope to use my Ext-HDD as a "Linux-to-Go" drive. (Get it? Windows-to-Go?)

Thanks!

---

### Post by ubfan1 on 2013-07-20
Maybe totally wrong, as my Mac experience is 0, but the efi boot entries are for the hard disk, and devices, so choose USB (or just make USB first in boot order).  Check the USB's EFI partition, I find the grub install tends to ignore the target's efi and grabs the hard disk's.  Just copy over the files from the hard disk if the target EFI partition is empty.  Check that the EFI/Boot/bootx64.efi (? boot{architecture} so may not be x64 for you) is the same size as /EFI/ubuntu/shimx64.efi (it should be a copy of shim), and that there is also a /EFI/Boot/grubx64.efi  present (the 900k sized signed one I'd guess for you). There should be a /EFI/ubuntu/grub.cfg file for the grub menu, and that should be it.  I find running from USB works, but sometimes unexpected things happen on updates, like removing the valid hard disk Ubuntu efi boot entries (Maybe not an issue for you if no hard disk copy of Ubuntu).

---

