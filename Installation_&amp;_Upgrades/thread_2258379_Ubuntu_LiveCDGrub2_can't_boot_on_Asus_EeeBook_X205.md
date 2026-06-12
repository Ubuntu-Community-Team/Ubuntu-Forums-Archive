---
title: "Ubuntu LiveCD/Grub2 can't boot on Asus EeeBook X205"
date: 2014-12-27
forum: Installation &amp; Upgrades
---

### Post by clausen2 on 2014-12-27
I just bought an Asus EeeBook X205, which is a new model ultrabook from late 2014.  It comes with Windows 8.1 installed.  I have not yet been able to boot Linux in any form on it.

I think I have figured out why:
[LIST=1]
[*] The UEFI firmware does not support legacy BIOS. 
[*]The UEFI firmware seems to be 32-bit based (not 64-bit).  The EFI system partition contains a 32-bit boot file, named /EFI/BOOT/bootia32.efi.  (It's possible to access this by going to Windows 8.1's advanced boot menu, booting into the rescue command prompt, mounting the system partition with mountvol S: /s, and then looking inside that by typing S: then CD EFI\BOOT then DIR.) 
[/LIST]

Apparently Ubuntu does not yet provide a 32-bit EFI boot loader, so I think the only way to proceed is to install my own 32-bit based boot-loader, as per [http://askubuntu.com/questions/392719/32-bit-uefi-boot-support](http://askubuntu.com/questions/392719/32-bit-uefi-boot-support).  Am I missing anything?

---

### Post by clausen2 on 2014-12-27
Apparently this is a well known problem (even though it isn't documented in the release notes or install guides).  These bugs are relevant: [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1025555](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1025555) and [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1341944](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1341944).

Potential work-arounds: [https://bbs.archlinux.org/viewtopic.php?id=179948](https://bbs.archlinux.org/viewtopic.php?id=179948) and [https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md).

---

### Post by oldfred on 2014-12-28
Just recently Linux kernel added support.
 Instructions to install Ubuntu 14.10 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)
Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)


 Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)
Some new 64 bit low cost systems with 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

Now older, recompile yourself:

 New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

 But someone has it partially working:
[http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html](http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html)
Asus T100 Compile own grub 32 bit
[http://ubuntuforums.org/showthread.php?t=2191557](http://ubuntuforums.org/showthread.php?t=2191557)

---

