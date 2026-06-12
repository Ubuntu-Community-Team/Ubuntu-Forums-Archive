---
title: "grub only shows up with ubuntu installation pendrive"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by Tulio Lages on 2012-11-14
Hi guys.

I installed Ubuntu 12.04 recently in my friend's notebook (dual-boot with Windows 7. And I didn't use wubi) and everything went smoothly. However, when we turn on the laptop, it boots directly to Windows 7. When I try to boot via the pendrive to reinstall or something else, the grub pops up. And last I checked, I didn't find any partition in the laptop with the MBR or grub. But every pendrive with ubuntu prompts the grub screen, not the installation one anymore. How do I make the grub show up without a pendrive? Thanks in advance!

---

### Post by darkod on 2012-11-15
But with the stick does it boot the installed ubuntu or the live mode from the stick?

If it boots the installed ubuntu, boot it once with the stick plugged in, open terminal and check the disks with:
sudo fdisk -l (small L)

That should show the hdd and the stick, probably /dev/sda will be the hdd and /dev/sdb the stick.

After you know which one is the hdd, use it in the following command:
sudo grub-install /dev/sdX

That will install it onto the MBR of the hdd. Reboot without the stick and see if you get grub2.

---

