---
title: "Fixing Booting Files while other HDDs r disconnected or not?"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2014-01-29
I just fixed my Windows 8.1 TWICE! Sure it was educational to learn 2 different ways to recover from this, but I'm not looking forward to learn a third way!
I'm trying to setup a dual-boot with Win8 & Ubuntu 13.10. I have Windows 8 in one HDD, Ubuntu on another, and there's a 3rd HDD for additional space. At the moment I just fixed the Win8 booting files, but I still need to do the same for Ubuntu.
For this 2nd time I had disconnected the 2 other HDDs I have. That might have been the reason why I succeeded fixing the Win8 booting files, not sure though.
So I was thinking that if I'm to do the same to fix the Ubuntu booting files I might be in a better position to succeed, as it has failed in the past while using Repair Boot Disk and with all the HDDs connected.
Assuming disconnecting the other HDDs is indeed a good idea,... wouldn't the booting files for either/both OSs get messed up again when connecting all the HDDs again?
Is this approach even worth the trouble? Or am I better off just reinstalling Ubuntu while all HDDs are connected? (I think the trick is to choose "other choices" or something like this when the installer asks you how to install Ubuntu, so that the installation is compatible with Windows 8).

---

### Post by oldfred on 2014-01-29
First is Windows in UEFI or BIOS boot mode?
And is Ubuntu in UEFI or BIOS boot mode?
Best if both are same boot mode.

Lets see details.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

BIOS boots from MBR. But you can have different boot loaders in each drive's MBR, but have to install that way.
UEFI boots from an efi partition. You can have only one efi partition per hard drive, but UEFI will find boot files on every drive.
And install with other drives disconnected forces each install to have its boot files on its hard drive which is a good thing. But with drives connected you have to preset or configure correctly. Or use Boot-Repair to reset afterwards.

---

