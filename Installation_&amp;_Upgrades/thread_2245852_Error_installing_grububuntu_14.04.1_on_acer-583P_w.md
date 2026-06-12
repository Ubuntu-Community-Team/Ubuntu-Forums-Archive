---
title: "Error installing grub/ubuntu 14.04.1 on acer-583P windows 8 dual boot"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by cortell on 2014-09-26
I am attempting to install Ubuntu 14.04.1 on a multi partitioned (i.e. recovery partitions) 500GB drive residing inside of an Acer m5-583p laptop with Windows 8 in with Dual Boot functionality. When i install ubuntu from a live usb everything works fine. But when i restart to boot it loads windows instead, i figured it was something wrong with grub not being installed correctly in the MBR of dev/sda so i mounted the linux file system and tried grub-install but it keeps giving me the following errors:

[COLOR=#000000][FONT=Arial]this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and their use is discouraged.
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]will not proceed with blocklists.[/FONT][/COLOR]

---

### Post by ajgreeny on 2014-09-26
Try Boot-Repair from my signature below, but **do not** at this stage run the repair, just run the boot-info-script and copy the link it gives you back here so we can read the report.

---

