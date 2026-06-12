---
title: "Install over Linux Mint 13"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by rickm1945 on 2012-06-28
What is the best way to install Ubuntu 12.04. I have LM13 Cinnamon on a dual boot system. After trying Ubuntu 12.04 I think I like the feel and GUI better than Mint.
:confused: What is the best way to install Ubuntu12.04?

---

### Post by darkod on 2012-06-28
It's really up to you.

If you are happy with the partition sizes you used in Mint, you can boot with the ubuntu cd, start the installation and use the manual method (Something Else).

All linux partitions are marked Not Used by default. You will have to select them one by one, depending how much you have, and set the correct mount point for that partition.

For the main root partition the mount point is /, the filesystem usually used is ext4. Tick the format box so that it deletes all of Mint.
For swap, the type is swap area and it doesn't use mount point and formatting.

If you were using a separate /home, use that partition as /home again, with or without formatting.

For the bootloader select the MBR of the disk, like /dev/sda (without any number in it).

Or, if you prefer, boot ubuntu into live mode, open Gparted and delete the Mint partitions. Then you can install as if you never had Mint.

---

### Post by rickm1945 on 2012-06-28
> **darkod said:**
> It's really up to you.

If you are happy with the partition sizes you used in Mint, you can boot with the ubuntu cd, start the installation and use the manual method (Something Else).

All linux partitions are marked Not Used by default. You will have to select them one by one, depending how much you have, and set the correct mount point for that partition.

For the main root partition the mount point is /, the filesystem usually used is ext4. Tick the format box so that it deletes all of Mint.
For swap, the type is swap area and it doesn't use mount point and formatting.

If you were using a separate /home, use that partition as /home again, with or without formatting.

For the bootloader select the MBR of the disk, like /dev/sda (without any number in it).

Or, if you prefer, boot ubuntu into live mode, open Gparted and delete the Mint partitions. Then you can install as if you never had Mint.

Thank you for your help, I just did a clean install from scratch.

---

