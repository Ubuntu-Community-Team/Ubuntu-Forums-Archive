---
title: "Upgrade 24.04 to 24.10 root= Error"
date: 2024-10-12
forum: Installation &amp; Upgrades
---

### Post by wdaytonland on 2024-10-12
I upgraded to 24.10 from 24.04 and now have a boot error. "VFS: Can not open root device "dev/sda3" or unknown-block (0,0) ....". The kernel line that is failing to run has this in it: "/vmlinuz-6.11.0-8-generic root=/dev/sda3" and none of the other command lines have the "root=" text in them. The previous kernel command line, that has no "root=" in the command line, still loads correctly. Grub already has a line "set root='hd0,gpt2'". Why does it have a root reference in the command line when there is already one before it in the "set root" line? I am not sure if the kernel upgrade to 6.11 happened when Ubuntu upgraded to 24.10 or not. I tried removing the "root=/dev/sda3" text by editing the command line at grub startup, but it failed when I did that (something about it needed a root= instruction) and I also tried different forms of "root=hd0" but those failed also. Please HELP! and Thanks.

---

### Post by Rubi1200 on 2024-10-13
Please boot from a live medium and choose to Try Ubuntu.

Then, follow the instructions for the boot info script in my signature to create a summary report with a pastebin link that you can post back here.

Once we see the script results it will be much easier to offer possible solutions.

---

