---
title: "I've just fixed several UEFI installation issues"
date: 2016-05-21
forum: Installation &amp; Upgrades
---

### Post by phoenix1963 on 2016-05-21
If you're installing (single OS boot) on two disks (SSD 60GiB for Linux, HDD for /home), you may face the same problems I've had on my ASUS H81 motherboard. I used an Ubuntu 16.04 DVD on the front of LinuxFormat to install (Live USBs can be very painful to get right). I hope this helps:

1. My SSD was mounting as /dev/sdb, the Ubuntu install will only work on /dev/sda. This may have generated the error "grub-efi-amd64-signed package-failed to install". Fix: I swapped the SATA cables around on the motherboard.
2. Having failed for months to get Ubuntu 14.04 to boot in UEFI mode (despite USBs happily booting that way), I realised today that the old 14.04 had installed in legacy (BIOS) mode and that therefore my SSD was formatted in old-style MBR partition mode. Now Rod [http://www.rodsbooks.com/gdisk/cgdisk-walkthrough.html]("http://www.rodsbooks.com/gdisk/cgdisk-walkthrough.html") has an excellent guide to using his utility to repartition as a GPT disk. Rod is a really great guy to have supplied all this stuff, but wow, it needs an "idiot's guide!"
So, the fix is, boot off a Rescue CD/DVD (this was helpfully on the same LinuxFormat DVD) that has cgdisk and use it to delete all the existing partitions on the SSD, then allocate the first as a 2GiB UEFI (type ef00) one; the second as a 30GiB Linux filesystem (type 8300); thirdly, the rest as Linux Swap (type 8200). Note that this is DIFFERENT from Rod's page above, because he's setting up a legacy (BIOS style) boot.
3. Use the commands:```
mkdosfs /dev/sda1
mkfs -t ext2 /dev/sda1
``` where /dev/sda is my SSD.
4. Then I'm ready to install Ubuntu and use the "do something else" option which gives you gparted where you can use the "change" button to assign uefi, /, swap and /home to the 3 SSD and 1 HDD partitions.

It installs perfectly, just took many hours of reading and fiddling!

I hope this helps,

phoenix

---

