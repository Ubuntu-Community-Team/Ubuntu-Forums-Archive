---
title: "Upgrade without installing boot loader"
date: 2020-05-24
forum: Installation &amp; Upgrades
---

### Post by gjohnz on 2020-05-24
While running Ubuntu 19.10 64 bit. i was offered an upgrade to Ubuntu 20.04. Offer accepted. Shortly after the upgrade started it stopped with the message

> EFI System Partition (ESP) not usable
 
Your EFI System Partition (ESP) is not mounted at /boot/efi. Please ensure that it is properly configured and try again.

Here's the deal. I don't care if the EFI or ESP is not usable. I don't want a bootloader installed. This is a multi boot system with 5 or 6 other Linux installations and I am using rEFind to boot the computer.

Don't want. Don't need. We do this the way I want it done or we format the partition and install something else.

How can I upgrade without installing a bootloader?

10 minutes later:

I manually mounted /boot/efi (was disabled in /etc/fstab by me) and am attempting upgrade through the command line. Installation of the bootloader, if we get that far, will fail, but that is OK. We shall see.

And about 30 minutes later still:

Well I answered my own question. The upgrade completed just fine. I'm editing this post from Ubuntu 20.04. The upgrade tried to install grub 3 times and failed. I chose to continue anyway even though "your system may be rendered unbootable" and all is well.

---

