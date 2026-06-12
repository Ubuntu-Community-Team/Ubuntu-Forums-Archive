---
title: "GRUB Problem"
date: 2020-09-13
forum: Installation &amp; Upgrades
---

### Post by jnmat on 2020-09-13
Hello.  I have a similar problem.  I uninstalled ubuntu by firstly, removing the partition via windows disk management and secondly, by using aomei partition assistant. 

However, I can still see ubuntu listed in the drop down menu of my laptop efi bootloader if I click on boot option #3.  If I pick ubuntu as any of the boot options either #1, #2 or #3, and if the laptop boots into ubuntu, a gnu grub version 2.04 message pops up  saying "minimal bash-like line editing is supported.... grub>_".

What do you guys think?  Do you think I have completely uninstalled ubuntu?  How do I remove the ubuntu option in the drop down menu?

---

### Post by coffeecat on 2020-09-13
Split from this thread: [https://ubuntuforums.org/showthread.php?t=2449216](https://ubuntuforums.org/showthread.php?t=2449216)

Please start your own threads. That thread was resolved.

---

### Post by CelticWarrior on 2020-09-13
OSes aren't really uninstallable. That said, once the system partition(s) is/are removed, it's obviously no longer there, can't possibly work/boot, but bootloaders are untouched in the ESP (EFI System Partition) and that's what you see.
How to manage bootloaders and boot order from Ubuntu is typically done with the efibootmgr tool.**How the same is accomplished from Windows is a good question for Windows forums, don't you think?** I can suggest EasyUEFI but the good folks at Windows forums likely will suggest something better.

---

### Post by oldfred on 2020-09-13
There are ways with Windows to also remove UEFI boot entry & /EFI/ubuntu folder in ESP.

But with Linux:
Delete Ubuntu
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)
UEFI How To Remove Ubuntu From A Computer Dual Booting With Windows 10 (UEFI only)
How To Remove Ubuntu From A Computer Dual Booting With Windows 10
[http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html](http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html)
Delete /EFI/ubuntu folder from Windows
[http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/)

Uninstall Ubuntu from menu, Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi) &
[https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader](https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader)

---

