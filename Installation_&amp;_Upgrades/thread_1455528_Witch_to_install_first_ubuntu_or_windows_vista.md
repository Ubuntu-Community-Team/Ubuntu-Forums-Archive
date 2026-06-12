---
title: "Witch to install first ubuntu or windows vista ?"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-04-16
I have always use dual-booting vista--ubuntu, I am getting bit tired of windows, so I want to install ubuntu, specially lucid is coming soon. I want to have the posiblity to install windows in case I will need it in the future, like working with Visual Studio, ubuntu always detect if windows is installed, if windows is installed first, does windows also detect if ubuntu is installed ?

---

### Post by sum1nil on 2010-04-16
Hi,
I'm not a guru, but I've had better luck installing the windows os (in my case windows 7) and then installing ubuntu. This way grub is written as the loader, while if you do windows after ubuntu, you will have the windows loader only. As far as I can tell, windows 7 doesn't even know I have ubuntu installed ie it does not see linux drives.

Hope this helps

---

### Post by new_tolinux on 2010-04-16
> **sum1nil said:**
> Hi,
I'm not a guru, but I've had better luck installing the windows os (in my case windows 7) and then installing ubuntu. This way grub is written as the loader, while if you do windows after ubuntu, you will have the windows loader only. As far as I can tell, windows 7 doesn't even know I have ubuntu installed ie it does not see linux drives.

Hope this helps
+1

I did it that way with Windows 7 / Ubuntu 9.10 and later Win7/OpenSuse after removing only the Ubuntu partitions (left Grub, because I hoped it would be replaced by OpenSuse, which it did).

But I'm not an expert either ;)

---

### Post by jmore9 on 2010-04-16
I have always install windows first then linux.  That way grub or lilo will find both at install.

---

### Post by hoboy on 2010-04-16
Ok if I read correctly the mails no one has done it in the way 
install ubuntu first then later install windows ?

---

### Post by balaram on 2010-04-16
I've done it both ways. Installing Windows first is easier. If you install Windows last you'll then have to reinstall the Grub2 or Grub Leagcy bootloader (depends on what version of Ubuntu you install) because the Windows bootloader won't recognize Ubuntu. Reinstalling Grub is pretty simple if you're an experienced Linux user but for a newbie it is a bit confusing.

---

### Post by hoboy on 2010-04-16
> **balaram said:**
> I've done it both ways. Installing Windows first is easier. If you install Windows last you'll then have to reinstall the Grub2 or Grub Leagcy bootloader (depends on what version of Ubuntu you install) because the Windows bootloader won't recognize Ubuntu. Reinstalling Grub is pretty simple if you're an experienced Linux user but for a newbie it is a bit confusing.

Tks

I am planing to install 10.04 LTS when it is realised

---

### Post by presence1960 on 2010-04-16
> **hoboy said:**
> Ok if I read correctly the mails no one has done it in the way 
install ubuntu first then later install windows ?

You can most definitely install windows after Linux!

The reason most people do it the other way is they are lazy and/or do not understand what happens when you install windows after linux. let me explain:

When you install windows after linux windows overwrites GRUB on the MBR with it's bootloader. So when the windows installation is complete and you reboot your machine you boot straight to windows. At this point most people panic and think their linux install is gone for good!

Not so. All that is needed is to reinstall GRUB to MBR so when you boot you are given the GRUB menu and can then choose to boot either linux or windows.

The statement that windows must be installed before Linux is FALSE.

Here are some links to read on the matter:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

That being said it is truly a matter of personal preference which order you wish to install windows & linux. But don't be fooled into believing you must install windows first. You don't need to remove a perfectly good linux install (or make an image and restore it) just to install windows on a machine that already has linux.

---

### Post by hoboy on 2010-04-17
> **presence1960 said:**
> You can most definitely install windows after Linux!

The reason most people do it the other way is they are lazy and/or do not understand what happens when you install windows after linux. let me explain:

When you install windows after linux windows overwrites GRUB on the MBR with it's bootloader. So when the windows installation is complete and you reboot your machine you boot straight to windows. At this point most people panic and think their linux install is gone for good!

Not so. All that is needed is to reinstall GRUB to MBR so when you boot you are given the GRUB menu and can then choose to boot either linux or windows.

The statement that windows must be installed before Linux is FALSE.

Here are some links to read on the matter:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

That being said it is truly a matter of personal preference which order you wish to install windows & linux. But don't be fooled into believing you must install windows first. You don't need to remove a perfectly good linux install (or make an image and restore it) just to install windows on a machine that already has linux.


Tks everybody.
As I said in my mail I want to investigate if it was problem to install linux then later when the need comes to install windows on the same machine I can do it without lots of problems.I get the answer.

---

