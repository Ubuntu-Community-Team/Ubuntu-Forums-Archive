---
title: "Ubuntu 21.04 installer hangs on install"
date: 2021-09-23
forum: Installation &amp; Upgrades
---

### Post by docholiday520902 on 2021-09-23
HP tg01-1160xt
i5-10400 
Integrated GPU - (originally configured with external, was removed)
HDMI out
Custom motherboard - unknown

Booting for USB, made several different times with different USB using different apps (rufus, unetbootin, etc). 

Tried 21.04 as well as the newest alpha, can't seem to progress past the selection point in GRUB - doesn't matter what I choose. Shows Ubuntu logo beneath HP logo and then hangs. Seems like graphics is hanging and I suspect everything else is still working. When showing text in boot process it seems to hang at random moments as well. Disabled fastboot, secure boot, nomodeset added, etc. Tried another monitor, doesn't make difference. Came with Win10 which works fine.

Any ideas?

---

### Post by oldfred on 2021-09-23
Have you turned off Optane or Intel RST and set drives to AHCI?

HP 15 disable Optane
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483) & 
[https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10](https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10)
HP 17-BY4063CL Laptop shows UEFI screens, needed 21.04 since new Intel chip
[https://ubuntuforums.org/showthread.php?t=2462045](https://ubuntuforums.org/showthread.php?t=2462045)

See also list of common issues:
[https://ubuntuforums.org/showthread.php?t=2467343](https://ubuntuforums.org/showthread.php?t=2467343)

---

