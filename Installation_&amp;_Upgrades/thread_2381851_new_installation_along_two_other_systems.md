---
title: "new installation along two other systems"
date: 2018-01-06
forum: Installation &amp; Upgrades
---

### Post by jarp53 on 2018-01-06
i want to install Ubuntu in it's own 60 GB ssd  , i also mint and windows in separate 60 GB ssd's ; so when i go to install and choose " erase disk and install " is it going to give the choices or do i have to use " something else " ; or is it better to just unplug all the drives and just leave the disk that i want to use only

---

### Post by yancek on 2018-01-06
If you don't have much experience, it would probably be better to unplug the other SSD's so you don't accidentally overwrite one of the other systems.

The Something Else option is always better to use as you have control over what is happening.
Which windows are you using?  Are windows and Mint both UEFI or MBR?

---

### Post by RobGoss on 2018-01-06
You can also use the Windows disk management tool to create a **Unallocated **partition for your new Ubuntu installation. When you come to the option to choose Something Else, you can then pick that partition you created for Ubuntu

I strongly suggest you use **Yancek **advice and unplug the other SSD's just as a safety rule to secure your data on the SSD's

You might even want to make sure your data is backup as well

---

### Post by jarp53 on 2018-01-06
i was going to unplug , just wanted to make sure it wouldn't create start up problems, and already look into grub upgrade , so thanks again for your quick response

---

### Post by oldfred on 2018-01-06
If system is UEFI, unplugging a drive will remove the UEFI entries as drive is not there.
Some systems parse ESP to find boot entries, but they usually only find Windows.
But you can easily use efibootmgr to add entries.
Or last install's grub will offer to boot all those entries. Although I like to keep multiple ways to boot, so want entries in UEFI also.

See:
man efibootmgr

Example for Windows:
 This should create a new entry, if ESP is sda1, uses defaults:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"
if ESP sda2, you have to specify drive & partition
sudo efibootmgr -c -d /dev/sda -p 2 -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

---

