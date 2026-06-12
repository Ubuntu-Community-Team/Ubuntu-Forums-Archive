---
title: "Install location"
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by bgswanson on 2011-11-26
Finally got ubuntu up and running. It's not where I want it though. Right now it's installed on PC's master HDD which is the C drive along side windows xp. I have an additional HDD installed internally (H drive) where I would like to move this OS to. Currently windows and ubuntu boots from the C drive. I would like to keep windows for the time being to boot from the C drive and want ubuntu to boot from F drive. Right now using boot priority in bios settings to switch between the two is fine with me. I do have it still on the USB and on a dvd rw but I would rather move it from within the desktop since I'm not even sure which method worked when I installed it. Anyone have any ideas on how I should go about this?

---

### Post by darkod on 2011-11-26
I would say use the usb stick to boot and install it like that. If there are any issues during the install they would be the same regardless of the install media.

When it asks you where you want it installed just select the hdd you want as destination. You can either use manual partitioning or one of the auto methods. Just make sure you select the correct hdd especially if you use the 'erase and use whole disk' option.

If at the moment you are booting the XP and the current ubuntu from grub2, make sure you hold on a bit with deleting the partition of the ubuntu on the first hdd because it will become unbootable.

And having said all this, I hope we are talking about a proper dual boot and not wubi.

---

### Post by bgswanson on 2011-11-26
> **darkod said:**
> I would say use the usb stick to boot and install it like that. If there are any issues during the install they would be the same regardless of the install media.

When it asks you where you want it installed just select the hdd you want as destination. You can either use manual partitioning or one of the auto methods. Just make sure you select the correct hdd especially if you use the 'erase and use whole disk' option.

If at the moment you are booting the XP and the current ubuntu from grub2, make sure you hold on a bit with deleting the partition of the ubuntu on the first hdd because it will become unbootable.

And having said all this, I hope we are talking about a proper dual boot and not wubi.

That's the thing, on the last install I don't recall it ever asking for location. Is it as simple as right-clicking on the icon and saving it in the F drive, then navigating to that location and opening it up there? I'm really not sure if I'm booting from grub2 but assume that I am since the version is 11.10. I don't plan to wipe the C drive clean until I am very familiar with Ubuntu. This is my first exposure to it.

---

### Post by darkod on 2011-11-27
It's impossible not to ask you about the location.
One reason might be if you have ever used the second hdd in a RAID and it has meta data left on it. Formatting doesn't destroy that as many people think. The Ubuntu installer ignores disks with meta data so it might look like you have only one hdd. In that case why would it ask you where to install.

Boot your working ubuntu and check the disks and partition with:
sudo fdisk -l (small L)

If the second disk is for example /dev/sdb, to make sure there is no meta data run:
sudo dmraid -E -r /dev/sdb

If it asks if you want to remove the meta data, you have it. Just confirm and the disk is ready for ubuntu to be installed.

The bottom line is, if both hdds are discovered properly, there is no way not to have the option to select where to install. If you are not getting it, something is not right.

---

