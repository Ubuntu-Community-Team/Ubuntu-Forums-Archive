---
title: "GRUB update installed bootloader in Windows EFI partition."
date: 2020-04-15
forum: Installation &amp; Upgrades
---

### Post by warren3 on 2020-04-15
Well it was my fault really.

I've got a dual boot running.  sdb2 is Windows EFI and I when I installed 20.04 yesterday I placed GRUB in 125MB EFI partition at sdb5.  Now I have come to update just now and GRUB needed updating and gave me an option of where to place the bootloader.  I picked sdb2 by accident.  'Oh s**t'  I thought. Anyway I rebooted and everything was working OK.

Is there any way to get the bootloader back to sdb5 or is it OK living in the windows EFI partition?

Cheers.

---

### Post by oldfred on 2020-04-15
You are ok.
You should have two folders in ESP, one ubuntu & one Microsoft, each with its own boot files.

Not sure it would have worked with two ESP, on one drive??
I have seen users with two FAT32 formatted partitions and UEFI only boots one, and grub does not care if flagged as ESP, so finds boot files in other. But almost all UEFI only will boot from one ESP per drive. You can have an ESP on every drive also.

You may want to check UEFI entries.
sudo efibootmgr -v
It will show GUID of ESP it uses to boot from.
This shows GUID, but is called partUUID.
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"
If you have entries from old ESP, you can delete with efibootmgr.
man efibootmgr
sudo efibootmgr -b XXXX -B

---

