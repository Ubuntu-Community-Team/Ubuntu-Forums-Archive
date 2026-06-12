---
title: "GRUB-Install help.."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by hopestorm on 2007-04-21
I reinstalled my windows and try to reinstall GRUB. 
Boot into Ubuntu installation CD, and :
>>sudo grub-install /dev/hda

and I was told: could not find device for /boot: Not Found or not a block device.

I read a lot of similar complains online, and many suggest that The XP installer changed my partition and make the Grub-install doesn't work. SO I need to change /etc/fstab and /etc/mtab files, but I don't know how to do it.
SOmeone can help?

Thanks,

---

### Post by Dirty Ole on 2007-04-21
Try [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation")

After you have done that use grub-install on the same drive. I reinstalled windows too and this worked for me.

---

