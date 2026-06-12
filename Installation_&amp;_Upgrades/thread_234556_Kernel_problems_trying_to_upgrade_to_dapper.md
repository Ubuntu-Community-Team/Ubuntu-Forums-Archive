---
title: "Kernel problems trying to upgrade to dapper"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by kbabyxx on 2006-08-11
I'm trying to upgrade from Hoary to Dapper. [http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake](http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake) advices to go from hoary->breezy->dapper. I went from hoary->breezy ok. However when trying to go to dapper something has gone terribly wrong.

I changed my sources.list file and ran apt-get update then apt-get upgrade and finally apt-get dist-upgrade. When I rebooted the kernel options in grub were 2.6.8.1-3-k7 and 2.6.8.1-3-386. I get a message that kernels older than 2.6.10 are not supported. The boot process hangs at "starting hotplug system". The only kernels I can find in /boot are the 2.6.8 versions.

How can I solve this problem short of re-installing ubuntu and losing the data in my home directories?

---

### Post by mlind on 2006-08-11
Did dist-upgrade install dapper's kernel for you? grub probably didn't update the menu entries, so you need to manually run **update-grub**.
On grub menu, edit the first kernel entry and change kernel and initrd entries to point 2.6.15-26-k7 instead.

You can access to interactive mode and use TAB autocompletion to see what kernels are installed on /boot (partition).

Alternatively, you can boot into recovery mode using Ubuntu install cd (Desktop/Alternate) and chroot into your root partition. Then run dist-upgrade once to make sure that newer kernel is present and finally run update-grub.

---

### Post by kbabyxx on 2006-08-12
Thanks for the tip. I had tried something like that but missed the chroot step. I've already taken the easy way out - I backed up my home directory, reformated the drive and installed dapper.

---

