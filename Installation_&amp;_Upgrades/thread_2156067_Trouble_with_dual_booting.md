---
title: "Trouble with dual booting"
date: 2013-06-20
forum: Installation &amp; Upgrades
---

### Post by pasapas on 2013-06-20
Hi all,

I have searched the forums extensively and somewhat successfully installed Ubuntu 12.04 LTS alongside Windows 8.  I say somewhat successfully because occasionally I get an error when trying to start up Ubuntu from the Windows boot manager.  It says that \ubuntu\grubx64.efi cannot be found or something along these lines.  This only happens sometimes, oddly enough.  Sometimes, everything boots just fine.

Also, I fixed GRUB2 with Boot-repair posted in this sub-forum, and tried using EasyBCD to fix my problems, but to no avail.  In fact, I suspect EasyBCD caused this problem in the first place by pointing the windows boot loader to the wrong file.  Since GRUB2 works, I CAN boot Ubuntu from there, but Windows boot loader is much prettier :)  Besides, it bothers me that something is pointing to the wrong place.  Any advice would be appreciated.

---

### Post by fantab on 2013-06-20
I don't know much about EasyBCD but I think in order to use EasyBCD you will have to install GRUB to the Ubuntu partition and not on the HDD. I am not sure, please double check on EasyBCD forums.

---

### Post by oldfred on 2013-06-20
I think with UEFI, multi-booting is a lot easier as you can have many boot loaders all in the efi partition and each is a full boot loader and can chain load from one to another. Grub easily chain loads back to Windows, not exactly sure how EasyBCD does it.

With the old BIOS, you could only have one boot loader in the MBR to boot from and needed to stuff other boot loaders somewhere to be able to chain load to them.

---

### Post by pasapas on 2013-06-23
Thanks for the replies.  I don't want to give up on this, does anyone know how I can find the proper file to specify where to boot from?

---

### Post by oldfred on 2013-06-23
Post a link to BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by ubfan1 on 2013-06-24
For secure boot enabled, the path should be /EFI/ubuntu/shimx64.efi (and signed copy of grubx64.efi and grub.cfg should be in the same directory)
Without secure boot enabled, the path should be /EFI/ubuntu/grubx64.efi (with grub.cfg in the same directory)
My signed copy of grubx64.efi is 933752 bytes, while the unsigned copy is much smaller.  I'm not familiar with the Windows boot loader, so don't know how you would use that info.

---

### Post by pasapas on 2013-06-30
Hi all,

I am abroad and am unable to load onto a liveCD from here.  I can say that I turned off secure boot, so I will try pointing to that path that you specified.

---

### Post by darkomano on 2013-07-01
EasyBCD cannot create loaders for UEFI/GPT booting.
Windows UEFI boot manager cannot chainload "foreign" non-Microsoft boot managers/loaders.

a) Dual-booting Windows 7/8 and Ubuntu using UEFI/GPT can be done using UEFI firmware boot manager 
(both boot managers/loaders are placed on EFI System Partition)
OR
b) using GRUB2 which is capable of chaining Windows UEFI boot manager
(again both boot managers/loaders are placed on EFI System Partition)

-------------------------------------------------
BIOS/MBR booting is another story.
EasyBCD uses "grub4dos" in Windows for chaining GRUB.

But EasyBCD fails to state clearly that it is using grub4dos and so violates grub4dos GPL copyright.

---

