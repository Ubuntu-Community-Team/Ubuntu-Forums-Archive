---
title: "GRUB won't load after upgrade to Windows 8.1"
date: 2013-11-15
forum: Installation &amp; Upgrades
---

### Post by cmuluna on 2013-11-15
I had a dual boot setup with Ubuntu 13.10 and Windows 8, and it was working. I was able to log into Ubuntu as it was on the top of the boot order, but I logged in through Windows through the Windows boot manager. However, when I tried to log into Ubuntu after the 8.1 upgrade, I got an error stating that my Ubuntu was unable to boot because it was insecure.

I tried to fix the Ubuntu installation with Boot Repair. From that point forward, I see no GRUB and no error message. My computer simply skips Ubuntu as the first boot item and instead goes to Windows. I have tried Boot Repair twice, and below is the latest result. I currently have Secure Boot disabled and UEFI set to hybrid with Legacy Mode.

paste.ubuntu.com/6423449

Thank you for your help!

---

### Post by oldfred on 2013-11-15
You are showing two efi partitions, you can only have one. Actually I guess spec does allow more than one, but nobody works with that yet.
Use gparted and remove boot flag from sda6. With gpt partitioning the boot flag is supposed to only be on the efi partition. Actually it just is gparted/parted that uses boot flag, it is internal GUIDs that determine that the partition is the efi partition.

---

### Post by cmuluna on 2013-11-16
Thanks, oldfred! After I posted here, I tried turning UEFI back on (turning off Legacy in BIOS) and ran Boot Repair, except I checked the "purge" option.  I also happened to uncheck the "boot" flag in gparted as you mentioned.

This time I received the error mentioned here about the locked ESP with the read-only error: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477). I did not try any of the fixes for this report.

When I rebooted, I saw GRUB and am now able to boot into both Ubuntu and Windows. My assumption is that based on oldfred's comment, unchecking the boot flag was what fixed the problem.

Anyway....extremely happy to have Ubuntu back. I hope this helps someone.

---

### Post by oldfred on 2013-11-16
Glad you got it working. :)

---

