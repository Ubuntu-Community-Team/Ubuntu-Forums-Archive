---
title: "Tri-boot to dual-boot"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by ChunkyDrew on 2012-12-13
I have been tri-booting Windows 7, Windows 8 Release Candidate, & Ubuntu 12.04 LTS for a few months now. I have decided that, since I have no touch screen, i will not purchase Win 8. I now want to get rid of the Win 8 RC, then add that partition space to my Ubuntu partition, but have no idea how to accomplish this. 
Do I need to uninstall Win 8 RC from within Windows first? The grub loader sends me to the Win 8 loader, where I have Win 7 as the default. Does that complicate things?
Any assistance anyone can give would be greatly appreciated...:confused:

---

### Post by oldfred on 2012-12-13
Best to post details using BootInfo report. You can run from your install, liveCD/DVD/Flash or download a full ISO.

Windows may have installed its boot files in one or the other copy but then you have no boot files in the other. If boot files are in Windows 7, it will still be reported as  Windows 8 as it has & uses the Windows 8 boot files.
Might be easier just to make old Windows 8 a data partition. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

