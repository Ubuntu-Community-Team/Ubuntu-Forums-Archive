---
title: "Messed up my GRUB - Boot-Repair not working [Pastbin Added]"
date: 2018-09-13
forum: Installation &amp; Upgrades
---

### Post by shivahaze on 2018-09-13
What's up guys,

I was setting up my computer yesterday and lost myself in the process of customizing my Ubuntu.
Sadly it seems that I've managed to change/adjust something that must've killed my GRUB.
I realized something was broken on random restart when the GRUB-Menu didn't appear anymore but a straight boot into Windows 7 did.
I checked my boot order in the BIOS and also tried to manually boot into the GRUB but every time I end up in Windows in the end.

I have the USB-Stick I installed Ubuntu from and am now "trying Ubuntu" to get some kind of access. In this Process I tried Boot-Repair but without any success.
I thought I'd share my PasteBin and hope for the best, thanks alot in advance! 

[http://paste.ubuntu.com/p/CRVtJYXWJZ/](http://paste.ubuntu.com/p/CRVtJYXWJZ/)

Best wishes!

---

### Post by oldfred on 2018-09-13
You have now installed grub to MBR for BIOS boot, but it will not boot as you really have UEFI boot.
      

I have never seen this:  >  ** Warning ** : Bootffff is not EFI 1.10 compliant (lowercase hex in name)
** Warning ** : please recreate these using efibootmgr to remove this warning.
/usr/share/boot-sav/bs-cmd_terminal.sh: line 160:  8766 Segmentation fault      (core dumped) LANGUAGE=C LC_ALL=C sudo efibootmgr -v 

    

All UEFI are at version 2 or more. Apple Mac used EFI which is now version 1 of UEFI, but it also has been updated. And generally lowercase is used.

What brand/model system?

I might install the latest UEFI from your vendor. If not updated it should be anyway. Or if current, reinstall it. But any settings changes you made in UEFI like fast boot off, Secure Boot off etc, you will need to redo.
Then post this from live installer:
sudo efibootmgr -v

---

