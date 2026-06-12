---
title: "r/w access denied with Live CD"
date: 2014-04-14
forum: Installation &amp; Upgrades
---

### Post by Edelfelt on 2014-04-14
Hi!

I have Win XP and Ubuntu 12.04 LTS. As I had some partition problems, I used testdisk to write a new partition table.
The 2 Windows drive were in good shape, as well as the Home on Ubuntu. Root on Ubuntu had no files!

When rebooting I had a grub message. I started Live CD and in a terminal I typed:
sudo mke2fs -n /dev/sda6
which gives me the list of the superblocks available.

But when I type e2fsck -b "block number"  "device", I have the message:
You must have a r/w access to the files or be root.

How can I have access to the drive ?

Note that when I use Gparted, I have no partition allocated, but the 2 Windows partitions can be reached and used, as well as my Home!

This means that I can't reinstall Ubuntu, as it doesn't detect Windows XP.

Anyone an idea?

thanks for your help.

---

