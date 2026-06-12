---
title: "XOSL + Ubuntu 10.04 LTS"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by jwestbury on 2011-10-27
I'm working on a solution to create an automated recovery partition for Windows machines. My current idea is to use a stripped-down 10.04 install (currently trying with TurnKey Core) + ntfsclone to create and restore images of a Windows partition.

On my test machine, I've got a 250GB partitioned as follows:

/dev/sda1 - 30MiB partition for XOSL
/dev/sda2 - ~225GiB NTFS partition for Windows
/dev/sda5 - ~12GiB ext4 partition for Ubuntu
/dev/sda6 - ~500MiB swap partition

My installation process is as follows:

(1) Install XOSL.
(2) Install Windows.
(3) Repair XOSL.
(4) Install Ubuntu, with grub installed to /dev/sda5.

Now, based on guides I've found, this should work. And, indeed, I can boot Windows with XOSL. But when XOSL tries to boot my Ubuntu partition, I am brought to a blank screen with a flashing cursor, and grub never does anything.

FWIW, I've tried using XOSL to boot /dev/sda5 (the logical partition) as well as the primary partition on which it resides -- both yield the same result.

I know XOSL is pretty old at this point, so I'm not sure if anyone will be able to help.

If anyone knows of another way to set up a hotkey-based recovery partition for a Windows machine (boot Windows by default, boot Linux only when a hotkey is pressed at boot), I'd be glad to hear it.

---

