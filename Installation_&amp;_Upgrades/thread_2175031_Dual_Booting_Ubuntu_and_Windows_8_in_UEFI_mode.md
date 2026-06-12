---
title: "Dual Booting Ubuntu and Windows 8 in UEFI mode"
date: 2013-09-17
forum: Installation &amp; Upgrades
---

### Post by dshgna on 2013-09-17
Hi! 

I have googled and read several articles and forum posts on this topic, which unfortunately confuse me more. All help is greatly appreciated.

I have installed Ubuntu 13.04 on my WIndows 8 pre-installed Samsung laptop, with FastBoot and UEFI disabled and in Legacy mode. I used the guide here : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI). It has been working perfectly without any fault. However Windows was inaccessible from the grub loader, which I put down to it being in UEFI mode. It didn't matter much as I have shifted to Linux as my primary OS.
 
What I want to do now, is to dual boot both in UEFI mode. I need Windows now to do some .NET development(Yes I know there is Mono but I prefer using the original OS)! My approach was to go back to UEFI mode, access Windows 8, install Ubuntu in UEFI mode and then live happily ever after :D! But seems I had missed some really salient points.

So, I tried entering BIOS on startup, but BIOS does not load! It simply jumps to the Ubuntu grub loader.

What can I do to remedy this situation?

Thanks very much :)!

---

### Post by oldfred on 2013-09-17
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

If you ran Boot-Repair, and it saw a buggy UEFI/BIOS it may have renamed your Windows efi file. You can unrename.

 Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

### Post by dshgna on 2013-09-17
Thank you very much oldfred.

But I finally discovered the bios key can be reached by F10, and in EFI Mode with Fast and Secure Boot enabled, Windows 8 just works fine.

So my question now would be on how to make Ubuntu boot in UEFI as well.

I guess I will have to remove my existing installation. Will get back to you soon on in this thread.

Thanks again :)!

---

### Post by oldfred on 2013-09-17
If you had not run Boot-Repair, grub2's os-prober does not create correct chain load entries from the grub menu. Boot-Repair does or you can manually add correct entries as shown in bug report.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry from os-prober that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

### Post by dshgna on 2013-09-24
Hi again,
Windows 8 and Ubuntu 13.04 run in perfect harmony after running boot repair.
However I still have two small niggles:

Boot repair asks to turn off secure boot in the BIOS. 

> Please disable Secure Boot in the Bios. Then try again.

When I turn off secure boot, Windows 8 boots properly. If not the error pops up. My question is on how to still keep SecureBoot and load Win8.

I don't know whether it is important, but when I start Boot Repair the following message pops up:

> efi detected. please check the options

I am clueless of what this means!

As always, all help is greatly appreciated.

Thanks ;)

---

### Post by oldfred on 2013-09-24
If you boot Boot-Repair with secure boot on, it will update to signed kernels for Ubuntu and then you can boot everything with secure boot on, if you desire.

       One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.


 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

