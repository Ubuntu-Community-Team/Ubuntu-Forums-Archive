---
title: "Ubuntu no longer shows in GNU GRUB menu when booting"
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by sigma1119 on 2016-10-22
After installing a kernel update to fix hardware issues and after a restart, Ubuntu no longer shows in the GNU Grub menu.
I booted from a USB and ran boot repair. Boot repair hangs on "Purge kernels then reinstall last kernel nvme0np7 (ins). This may require several minutes..."

I let this run for several hours with no luck. I have created a BootInfo summary here [http://paste2.org/Y6haLEUW](http://paste2.org/Y6haLEUW)

If anyone could help I would be very thankful. If there is any additional information I could provide that would be helpful, please let me know.

---

### Post by oldfred on 2016-10-23
You were able to install with NVMe device, so I would think update should have worked.

       to see GUID/partUUIDfor each device, post with code tags to preserve formatting:
sudo lsblk -o +PARTUUID /dev/sda
sudo blkid -c /dev/null -o list 
sudo efibootmgr -v

    sudo parted -l

Only some of above was in Boot-Repair's report.

---

