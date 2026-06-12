---
title: "New Install, New SSD - UEFI advice"
date: 2024-10-20
forum: Installation &amp; Upgrades
---

### Post by steven103 on 2024-10-20
Hi everyone,

Long time lurker here. I have a Windows 10 laptop with an SSD running out of space. I plan to remove the SSD and replace it with a higher capacity drive. I will be installing Ubuntu -Mate on it. It will be a clean install with no need for windows dual boot.

I may need to swap back to my windows SSD a couple of times per year. Will my clean Ubuntu - Mate install affect the UEFI in any way that might make this difficult for me?

Are there any settings I should be aware of before swapping the drives?

Thanks,

Steven

---

### Post by yancek on 2024-10-20
If you install Ubuntu on the new drive, it would be simpler if you do not have the windows drive attached.  Make sure you boot in EFI mode to install Ubuntu EFI and it should create an EFI partition on the Ubuntu drive.  After installing, set the Ubuntu drive to first boot priority in the BIOS and with the windows drive attached, run sudo update-grub from Ubuntu which should detect windows and add it to the Grub boot menu.  If you had windows 10 installed EFI it will have its own EFI partition and when you want to boot it, you can either select the windows drive from the BIOS boot options or boot it from the Grub boot menu of Ubuntu.

---

### Post by oldfred on 2024-10-20
Most UEFI seem to forget UEFI boot entries when a drive is disconnected.
Often they auto find Windows boot, but almost never a Linux boot.

So best to have good backups.
And a Windows repair/recover flash drive just in case and an Ubuntu live installer to restore UEFI boot entry either manually with efibootmgr, full chroot reinstall of grub, or with Boot-Repair and its advanced mode to reinstall grub.

---

### Post by steven103 on 2024-10-20
Great, thanks for this!

---

