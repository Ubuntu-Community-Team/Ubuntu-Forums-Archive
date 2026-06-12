---
title: "Dual booting with 2 disks"
date: 2020-02-17
forum: Installation &amp; Upgrades
---

### Post by joshua-powers22 on 2020-02-17
I haven't used linux in a while, I want to install kubuntu 19.10 but on my pc secondary internal hdd, the main disk is a ssd for windows and core apps, I want the linux boot loader on the second drive (which also has games/apps/files for windows) so if I want to get rid of the linux install it won't leave me with an unbootable system. Can someone walk me through or at least point me to a post/documentation that can help me, pls

---

### Post by joshua-powers22 on 2020-02-17
Never mind, I figured it out

---

### Post by vidtek on 2020-02-17
Joshua-  Please mark it solved after detailing your steps for other newbies.

Tony

---

### Post by oldfred on 2020-02-17
You need to partition in advance and only use Something Else install option.

Ubuntu's Ubiquity installer has an old bug that only installs grub to first drive, usually your Windows drive. You can copy files & use efibootmgr & edit fstab, or just totally reinstall grub to sdb or Ubuntu drive.

If not yet installed there is this work around to have grub install to sdb or any external drive. You still have to manually edit fstab with correct UUID for sdb's ESP.
       Posted work around to manually unmount & mount correct ESP during install #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

---

### Post by joshua-powers22 on 2020-02-17
The solution was to make a small boot partition on the second drive and importantly it needs to be the first partition on the drive then you point the installer to install the bootloader on the small partition (sda2 in my case) this way my pc normally boots into windows 10 and if I want to go to linux I just press f12 during boot (the key will vary from pc to pc) to get a boot menu and select the second drive.

---

