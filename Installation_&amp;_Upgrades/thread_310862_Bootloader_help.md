---
title: "Bootloader help"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by vichar on 2006-12-01
i am having a operating system xp and ubuntu.xp at drive c: and ubuntu at d: when i re-install my xp](*,)  i've lost my grub bootloader as xp overites it with its own.now its only running xp and not SHOwing my other operating sys.
what to do to reistall bootloader to run ubuntu
or
may run ubntu through normal windows-xp bootloader

---

### Post by Digicrat on 2006-12-02
I like using the Windows boot loader to load grub for Linux.  This simplifies a lot of issues that can crop up in either windows or Linux.

[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/) - Under the Installation section, there are instructions here on how to configure the windows boot loader.

[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm) - Equivalently, this nice utility works well at doing the same thing.  Simply follow the directions to create the bin file using this windows program, add it to your boot.ini in Windows, and you should be good to go. [Edit: Forgot the link]

I've used this technique successfully on several installations in the past.


Of course, since upgrading Ubuntu to Edgy though, I'm having problems getting this to work using the same configuration as before . . . .

---

### Post by tommcd on 2006-12-02
You can reinstall grub with the ubuntu live CD like this:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
or with the alternate CD like this:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
If you ever reinstall windows again you can backup grub like this:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_back_up_and_restore_your_MBR](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_back_up_and_restore_your_MBR)
Hope this helps.
EDIT: in the future, get yourself a super grub disk to deal with these problems:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

