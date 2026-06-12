---
title: "EFI boot on hp pavillon"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by pascalfares on 2013-12-13
How to add ubuntu and (grub2) with a EFI boot.

I installed ubuntu but I need each time de do F9 to get an EFI menu. after choosing ubuntu the grub2 is lanched.

---

### Post by ajgreeny on 2013-12-13
All the info you need should be at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI).

Do you have more than one hard disk,and have you got the wrong one set as boot priority?

Read my linked page carefully and do everything it says. Dependent upon how you configured the UEFI system itself, there should be an answer there.

---

### Post by pascalfares on 2013-12-13
[IMG]http://pix.toile-libre.org/upload/original/1353511012.jpg[/IMG]I Have the same config as this one but "OS boot manager" launch directly windows8

here is the /boot/efi
 boot  EFI  GraphicsLib.Log

and /boot/efi/EFI
Boot  HP  Microsoft  ubuntu

---

### Post by oldfred on 2013-12-13
Do you have secure boot on or off?
Did you install Ubuntu in UEFI or BIOS boot mode. How you boot installer is how it installs. Link by ajgreeny shows both BIOS & UEFI boot screens.
Then can you change UEFI boot order to have ubuntu entry first?

Please attach screenshots with the paperclip icon in the advanced editor. You can take photos of your screens but have to reduce them in size to 800x600 approx. to be small enough to upload.

       Guide to Forum features:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
Forum do & don't
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

