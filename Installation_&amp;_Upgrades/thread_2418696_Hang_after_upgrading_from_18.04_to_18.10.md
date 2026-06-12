---
title: "Hang after upgrading from 18.04 to 18.10"
date: 2019-05-09
forum: Installation &amp; Upgrades
---

### Post by Edward_Diener on 2019-05-09
I did the graphical upgrade to go from 18.04 to 18.10. On the bootup screen for 18.10 I see the message:

"fsckd-cancel-msg: Press Ctrl-C to cancel all filesystem checks"

but nothing further happens and pressing Ctrl-C does nothing. I have a full backup of everything so I can always go back to 18.04, but does anyone know what might be causing my hang after rebooting to the upgraded version ?

---

### Post by hashen on 2019-05-10
when boot screen appears press Ctrl+Alt+F1 and login.

then
[U]TRY 01

[/U]sudo fdisk -l
identify the boot record. (Linux File System)
sudo fsck -f /dev/(harddisk address sdb1 or whatever)
Do it again if there were errors
then reboot.

[U]TRY 02
[/U]boot to a Ubuntu Live DVD Or USB
go to terminal 
sudo fsck -f /dev/sda4
sudo fsck -f /dev/sda1
sudo fsck -f /dev/sdb1
sudo fsck -f /dev/sda5

And Reboot

Or like in try 01 
Try to Revert the Upgrade (Acucally Its Downgrade:p)

---

### Post by Edward_Diener on 2019-05-12
> **hashen said:**
> when boot screen appears press Ctrl+Alt+F1 and login.

then
[U]TRY 01

[/U]sudo fdisk -l
identify the boot record. (Linux File System)
sudo fsck -f /dev/(harddisk address sdb1 or whatever)
Do it again if there were errors
then reboot.

[U]TRY 02
[/U]boot to a Ubuntu Live DVD Or USB
go to terminal 
sudo fsck -f /dev/sda4
sudo fsck -f /dev/sda1
sudo fsck -f /dev/sdb1
sudo fsck -f /dev/sda5

And Reboot

Or like in try 01 
Try to Revert the Upgrade (Acucally Its Downgrade:p)

TRY 01 did not work. I was able to do TRY 02 with a Ubuntu 18.04 boot disk but there were no disk problems and when I then attempted to boot 18.10 afterward the same hangup occurred. I restored my backups successfully and now I am in 18.04 again.

I think, from searching the Internet, that the problem may be a bug in the upgrade process when using proprietary video drivers for my NVidia GTX 960 graphic card. I do not recall switching to proprietary drivers from the generic ones, so maybe you might know how I can check what I am using in Ubuntu 18.04. Evidently the bug workaround seems to be changing back to the generic drivers for the upgrade and then, after the upgrade has been successfully installed, changing back again to the proprietray drivers. Of course I could be wrong about the cause of the problem I am seeing when upgrading from 18.04 to 18.10, but it definitely is not because of parttition problems on my 18.04 system.

---

