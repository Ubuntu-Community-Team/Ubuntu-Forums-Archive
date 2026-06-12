---
title: "Installation Error"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by ChasingShadowsz on 2012-10-17
Hi guys.

I am currently running Windows 7 Ultimate and wanted to get into Ubuntu 12.04.

EDIT: I recreated a partition for Ubuntu and the swap partition(these partitions are separate from the windows partition and the windows system partition.), however after the installation it asks me to restart. Upon restarting, my computer just boots into windows. It does not come up with the grub bootloader or the windows bootloader. What's going on?

Please help guys, and thanks in advance.
:)

---

### Post by bcbc on 2012-10-17
When you install Ubuntu directly (while booted from the USB) it's supposed to replace the Windows boot loader. It doesn't sound as though this happened because what you are describing is the Windows Boot Manager trying to boot your (uninstalled) Wubi install.

That's another problem. When you uninstall Wubi it's supposed to remove that Windows boot manager entry that links to Wubildr.MBR, but it didn't. Effectively this entry is useless to you and you should remove it manually:
[http://askubuntu.com/a/145605/14916](http://askubuntu.com/a/145605/14916)

So your issue is:
1. When you installed Ubuntu it failed to install the grub bootloader
2. When you uninstalled Wubi it failed to remove the Windows BCD boot manager entry

To see where you are at, I recommend running the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and posting the results so we can give you instructions for installing grub.

---

### Post by ChasingShadowsz on 2012-10-18
Ok, I just realized I had removed the Ubuntu folder from my partition, instead of actually uninstalling the "program" from control panel inside windows 7.

I dont have time now but perhaps I'll give installing another go tonight  and get back to you to see if this fixed the issue.

EDIT: I recreated a partition for Ubuntu and the swap partition, however after the installation it asks me to restart. Upon restarting, my computer just boots into windows. It does not come up with the grub bootloader or the windows bootloader. What's going on now?

Thx in advance again. :)

---

