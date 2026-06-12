---
title: "Dual boot ubuntu/windows 8"
date: 2014-03-08
forum: Installation &amp; Upgrades
---

### Post by dennis14 on 2014-03-08
I tried to dual boot ubuntu  on my windows 8 laptop but something went wrong. When i try to turn on  my computer it flashes efi error and goes to a black screen that says  GNU GRUB version 1.99-21ubuntu3.14. Any ideas on what to do?

---

### Post by dennis14 on 2014-03-08
I got this too at some point when trying to run boot repair: [http://paste.ubuntu.com/7057753](http://paste.ubuntu.com/7057753)

---

### Post by oldfred on 2014-03-08
It looks like the boot loaders you have install are three versions. You have a Windows boot loader in the gpt protective MBR for BIOS boot, but your system is UEFI. Do not boot in BIOS mode or boot Boot-Repair in BIOS mode.
You also show both standard and secure boot versions of the kernels installed. 

And it looks like you ran 'buggy' UEFI from Boot-Repair. That is for those brands that modify UEFI to only boot Windows. If you can directly boot the ubuntu entry from UEFI, you do not need that. Best to undo until we know for sure if really required. Then at least you can directly boot Windows from UEFI.

Better to say no on this:
       buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
And to undo it:
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Have you followed these?
      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

What vendor & model and what video chip do you have?
See link in my signature for many common issues.

---

### Post by dennis14 on 2014-03-09
Thank you! Ran boot repair with your suggestions and it worked!

---

### Post by oldfred on 2014-03-09
Glad that worked. :)

---

