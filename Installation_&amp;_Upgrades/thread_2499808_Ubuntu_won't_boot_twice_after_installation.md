---
title: "Ubuntu won't boot twice after installation"
date: 2024-08-11
forum: Installation &amp; Upgrades
---

### Post by hein7777 on 2024-08-11
I used Windows in the past, but now I have decided to change and install Ubuntu myself. I make live bootable use with Rufus for the latest Ubuntu version. after finishing the installation it tells me to restart. then I can use it for that time, but after that restarting it or closing it and reopening it fails.

There is no partition or anything I can find in the boot menu for boot too. It said, "Reboot and select the proper boot device". I have selected my HDD for priority and also I have tried such as manual partitioning.

What should I do? I can't just install Linux at this point. I have also tried Fedora and the same issue. So any detailed help would be great.

Thanks

---

### Post by Rubi1200 on 2024-08-12
We would need more information to try and help you.

Make/model of laptop/computer?
Specs. like RAM, graphics card, storage?

Did you verify the checksum of the ISO?
[https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview)

---

### Post by yancek on 2024-08-12
>  after finishing the installation it tells me to restart. then I can use it for that time,

Does that mean you reboot the computer then select the hard drive as  the boot option in the BIOS?  If so, then when you reboot it fails to boot?
Is Ubuntu the only OS on the computer?

>  "Reboot and select the proper boot device"

That means the bootloader was not properly installed.  Is this an EFI compatible computer and did you boot and install Ubuntu in EFI mode?

If you reboot the Ubuntu USB install media and run sudo fdisk -l or sudo parted -l, do you see partitions for the device?

---

