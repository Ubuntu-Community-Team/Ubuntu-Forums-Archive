---
title: "Installing Ubuntu from Flash Drive"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by michelleishell on 2010-01-10
Yesterday I installed Ubuntu Linux from a flash drive, and it worked perfectly. While I was on it, everything froze so I restarted, but when I restarted, the window to install Ubuntu from flash drive, or run it from flash drive, etc popped up even though I had already installed it. I chose to install it, but it wouldn't work. I tried to turn the computer on without the flash drive in, but it said to insert system disk, etc. I went into the Advanced BIOS and it was already set to first boot from harddrive. Can anyone help me?

---

### Post by darkod on 2010-01-10
Boot again with the flash drive, Try Ubuntu option, and in terminal check the partitions with:
sudo fdisk -l

Then run a check on the root partition with:
sudo fsck /dev/sda1 (or /dev/sda5, etc depending on fdisk results)

You might need to reinstall the bootloader too if it got corrupted. Instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

