---
title: "mounting issues on first boot (RAID1 configured during install)"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by prefabSOFT on 2010-09-24
Hi all,

I just thought I managed to configure my RAID1 during the Ubuntu Server install... (I also chose to use grubb in the end of the install btw)

But now I get this error when booting:

[INDENT]mount: mounting /dev/disk/by-uuid/c3c4608e-fb99-4989-bfe2-ede4aec72b38 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= boot arg

BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/INDENT]

Any ideas on what went wrong?

FYI, in the Raid config: I first created on both 500gb HD a 485.6gb partition of RAID type, then a 11gb partition of RAID type. Then I created a software raid for SDA1 mapped to SDB1, and SDA2 mapped to SDB2. Finally I created on my raid an EXT4 mapped to / and the smaller partition as a SWAP. (I feel like what I've done is correct though)

---

