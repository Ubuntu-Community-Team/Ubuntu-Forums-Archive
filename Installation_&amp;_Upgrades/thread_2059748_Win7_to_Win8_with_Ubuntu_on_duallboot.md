---
title: "Win7 to Win8 with Ubuntu on duallboot"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by Th3Alchemist on 2012-09-18
Hi!

I have Windows 7 and Ubuntu installed as dual-boot (not by wubi). And now I'm going to upgrade to Windows 8.

I got important work on my Ubuntu and already made backups, but can I upgrade my Windows 7 without affecting the Ubuntu partition?

(Thinking of formatting the Windows 7 and install Windows 8)

---

### Post by Laiquendi on 2012-09-18
You will most probably need to repair grub, but it's easy peasy :) Make sure you have some medium from which you can boot linux (like pendrive).

---

### Post by kaytrance on 2012-09-18
yeap, pretty easy, just [reinstall (or restore)]("http://odzangba.wordpress.com/2011/05/14/455/") grub after the installation.

---

### Post by Th3Alchemist on 2012-09-18
Even if I format Windows 7 to install Windows 8? (Instead of direct upgrading)

---

### Post by oldfred on 2012-09-18
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

Boot-Repair fixed BIOS boot Windows 8 & Ubuntu
[http://ubuntuforums.org/showthread.php?t=2056561](http://ubuntuforums.org/showthread.php?t=2056561)

Additional links with essentially the same instructions as posted above:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

Or a gui if you like:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Th3Alchemist on 2012-09-18
Thanks for the heads up

---

### Post by BrianBlaze on 2012-09-18
I had a lot of problems with this and although I probably could have re-installed grub again... I found the easiest way was to install Ubuntu last!

---

### Post by Vuk Serbia on 2012-09-18
Have you tried EasyBSD from within windows. I had problems trying to restore grub. It kept corrupting windows MBR.

---

### Post by Sir Hugh on 2012-11-04
Just wanted to added, in the hope that it might save someone some time, that I had restore the windows 7 bootloader before the upgrade would work.

The upgrade would run for about 20 minutes then get stuck. I went through this loads of times trying various things with no luck. I then tried restoring the windows 7 bootloader (put the windows 7 DVD in and repair startup), unplugged the drives with linux on (overkill probably but I'd become something of a maniac at this point) and ran the upgrade.

Afterwards I restored GRUB as everyone else is saying.

P.S. The grub windows 8 entry didn't work properly for me until I upgraded from precise to quantal. Never got round to figuring out why.

---

