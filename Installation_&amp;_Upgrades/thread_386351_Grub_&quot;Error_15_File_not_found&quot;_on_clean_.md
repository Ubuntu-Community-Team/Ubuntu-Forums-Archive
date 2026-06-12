---
title: "Grub &quot;Error 15: File not found&quot; on clean install"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by Kethinov on 2007-03-16
Upon doing a clean install of edgy, after I reboot and remove the LiveCD, Grub reports "Error 15: File not found" when booting any of the Linux kernel options.

My hard disk layout is like this:
/dev/sda (where Ubuntu is installed)
/dev/hda (storage)
/dev/hdb (more storage)

I rebooted into the LiveCD and examined the menu.lst. It was auto configured to look for a kernel at hd2,0 (/dev/hdb1) for some reason. I had to replace all references from hd2,0 to hd0,0 (/dev/sda1) before my system would boot from Grub.

This issue occurs every time I do a clean install. It also occurs in the new Feisty Fawn Herd 5 installer.

---

### Post by Kateikyoushi on 2007-03-17
Do you use both ata and sata drives ? In that case this bug is already reported but seems difficult to fix due to bios issues.

---

### Post by ernstblaauw on 2007-03-26
What kind of bugs does GRUB have when using ATA and SATA drives? I also have an error 15. I installed GRUB on my third SATA drive, and I have also one ATA drive. Now GRUB complains when I select Ubuntu to boot. Is a work around available? Which versions are affected?
I have a MSI K8N Neo2 motherboard.

I also started [a thread](http://ubuntuforums.org/showthread.php?t=393939) about this.

---

