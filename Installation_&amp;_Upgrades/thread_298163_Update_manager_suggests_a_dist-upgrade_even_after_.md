---
title: "Update manager suggests a dist-upgrade even after performing a cdrom upgrade"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by saurabhnanda on 2006-11-12
Hi,

I upgraded from Dapper to Edgy using the alternative install CD. I used the following command to upgrade:

$ gksu "sh /mnt/ubuntu/cdromupgrade"

The upgrade went ahead flawlessly (other than screwing up GRUB conf and not being able to boot with ACPI enabled). However, as soon as I logged in, the update manager in the system tray popped up saying that:

1. There were 278 updates available; and
2. Not all updates can be installed -- Run a distribution upgrade, to install as many updates as possible. This can be caused by an uncompleted upgrade, unofficial software packages or by running a development version.

What is going on? Is my upgrade incomplete -- as point (2) suggests -- can I safely ignore it? What should I do about point (1) -- I am not very confident of downloading 258 MB of packages not knowing whether I will have a usable system after it, or not (the distribution  upgrade was not a very comforting process, as it is!)

Any help regarding this will be highly appreciated!

TIA,
Nandz.

---

### Post by bulldog on 2006-11-12
Well,you have two choices,you can believe update-manager like I would do,or you don't update at all.

Take your pick wisely :D

---

