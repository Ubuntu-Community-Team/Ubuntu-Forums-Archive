---
title: "boot-repair for Windows 8"
date: 2015-02-08
forum: Installation &amp; Upgrades
---

### Post by valtert on 2015-02-08
Here I am, another user unable to boot Windows 8 after installing xubuntu 14.04

Here is the boot-repair log: [http://paste.ubuntu.com/10128628/](http://paste.ubuntu.com/10128628/)

I've tried grub-update and grub-install, which didn't work, then I've tried boot-repair with default options, which created this log.

I'll keep it as is until further help so I don't get it worse...

Thank for any help!

---

### Post by ubfan1 on 2015-02-08
Are you trying to boot Windows from the grub menu?  Still can't do that with secure boot on, (bug1091464). Try turning secure boot off.  Did you try the EFI menu choice for Windows (some function key at powerr-on, varies by machine)?  If you had performed the rename bootloaders in boot-repair, you might undo that, since your Windows EFI selection would then be grub instead of the Windows bootloader.

---

### Post by oldfred on 2015-02-08
Boot-Repair can only do minor repairs to Windows. And grub really only boots working Windows. So often you need to use a Windows repair Flash drive or third party Windows repair tools to fix Windows.

Did you leave it with the fast boot or always on hibernation set? That must be off.
You may be able to directly boot Windows from UEFI menu or one time boot key and with f8 get into a repair console?

Several similar ways for repair flashdrive:
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by valtert on 2015-02-08
Thank you, disabling Secure Boot solved the problem. Now I'm going to prevent Windows from hibernating and I think I'm done.

That's awkward, I thought Secure Boot would prevent Linux from booting, not Windows. This whole UEFI stuff is Greek to me. Booting Slackware from LILO decades ago was way easier ;)

Thanks for the quick response!

---

### Post by oldfred on 2015-02-09
I think it is a bug in grub. You should have been able to boot both Windows & Ubuntu from UEFI menu with secure boot on.
But currently secure boot is really only a Windows marketing tool.

---

