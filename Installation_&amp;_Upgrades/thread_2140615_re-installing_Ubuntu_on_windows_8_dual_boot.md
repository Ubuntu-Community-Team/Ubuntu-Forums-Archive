---
title: "re-installing Ubuntu on windows 8 dual boot"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by ubuntius on 2013-04-30
Hi, I have problems reinstalling Ubuntu 13.04.

I have previouslly installed with dualboot including using boot-repair, and everything worked fine.

But during an update from 12.04 to 13.04 something went wrong, so I decided to reinstall Ubuntu 13.04. But now I can not get booted into Ubuntu. It works fine to boot up in Win8.

I have chosen the same partitions that were joined during the last installation: root, swap and efi.

I've booted up via an Ubuntu USB and installed Grub Customizer, and when I, in Grub Customizer, choose  /dev/sda1 (which is efi partition), I get the following message: "*This seams not to be a root filesystem (no fstab found)* "

I got the following from the boot-repair: [http://paste.ubuntu.com/5619001/]("http://paste.ubuntu.com/5619001/")
... and a message saying: "*make sure that the BIOS boot from sda1/EFI/ubuntu/grubx64.efi*" ?

It is a ASUS S200E alptop

Does anyone know what I can do to get it working again. Let me know if I can give more details.

Thanks

---

### Post by oldfred on 2013-04-30
When you say it works fine to boot Windows is that from UEFI or grub menu?

I do not see anything in BootInfo report.

What video do you have? It may need extra boot paramters. Did you have to add any back with 12.10?

I do not know customizer, but it needs to know where grub is, not where grub boot loader is. Grub is in your Ubuntu ext4 partition, only the boot loader is in the efi partition. You can somewhat think of the efi partition as the replacement for the MBR in BIOS boot systems. 

The UEFI menu should have a ubuntu entry & a Windows entry. It looks like Boot-Repair did the rename of Windows files as some systems will only boot the Windows efi file. So Boot repair renames shim to be the Windows boot file and backs up the Windows efi file to chain boot from grub menu.

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi

---

### Post by ubuntius on 2013-05-02
Hi Oldfred, thanks for the reply. Bare over with me as i do not have that much knowledge on this - still learning.

> **oldfred said:**
> When you say it works fine to boot Windows is that from UEFI or grub menu?

I believe it is GRUB - i get the following to choose from:
Ubuntu
Advanced options for ubuntu
Windows UEFI bkpbootmgfw.efi - *this entry was not present the very first time i installed ubuntu alongside win8*
Windows boot UEFI loader
Windows recovery environment (loader) (on /dev/sda2)
Windows 8 (loader) (on /dev/sda4)
System systeup - *(it loads the BIOS settings)*

> **oldfred said:**
> I do not see anything in BootInfo report.
What video do you have? It may need extra boot paramters. Did you have to add any back with 12.10?

It is a Intel and when i installed 12.10 i did not need to add anything for the video card.

> **oldfred said:**
> I do not know customizer, but it needs to know where grub is, not where grub boot loader is. Grub is in your Ubuntu ext4 partition, only the boot loader is in the efi partition. You can somewhat think of the efi partition as the replacement for the MBR in BIOS boot systems. 

The UEFI menu should have a ubuntu entry & a Windows entry. It looks like Boot-Repair did the rename of Windows files as some systems will only boot the Windows efi file. So Boot repair renames shim to be the Windows boot file and backs up the Windows efi file to chain boot from grub menu.

Yes I have both Ubuntu & Windows entry. Is the renaming a problem? Should/can I do anything about it?

> **oldfred said:**
> 
       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi

I am not sure I understand what to do ....
My problem is i cannot see where BIOS is booting from - I have some instances in the BIOS menu, see below link:
[http://www.manualslib.com/manual/420816/Asus-S200e-User-Manual.html?page=69]("http://www.manualslib.com/manual/420816/Asus-S200e-User-Manual.html?page=69")

I have the following in the BIOS menu:
- Boot option #1: Window Boot Manager (PO: Hitachi HTS545032A7E380)
- Boot option #2: Ubuntu (PO: Hitachi HTS545032A7E380)

Regards

---

### Post by oldfred on 2013-05-02
From the grub menu what entries work.
Ubuntu should boot Ubuntu.

Windows UEFI bkpbootmgfw.efi should be the original Window efi file that grub chain loads back to boot with. Grub has to use shim when secure boot is on, and then you boot the secure boot Windows using this renamed file.

These two entries are from os-prober which still creates BIOS type entries that do not work with UEFI.
Windows recovery environment (loader) (on /dev/sda2)
Windows 8 (loader) (on /dev/sda4)

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)
    
So is secure boot on and ubuntu and/or Windows boot from grub menu?
Or do either boot with secure boot off.

---

### Post by ubuntius on 2013-05-02
> **oldfred said:**
> From the grub menu what entries work.
Ubuntu should boot Ubuntu.

Windows UEFI bkpbootmgfw.efi should be the original Window efi file that grub chain loads back to boot with. Grub has to use shim when secure boot is on, and then you boot the secure boot Windows using this renamed file.

These two entries are from os-prober which still creates BIOS type entries that do not work with UEFI.
Windows recovery environment (loader) (on /dev/sda2)
Windows 8 (loader) (on /dev/sda4)

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383) 

Thanks for the info - it gives me a 'little' better understanding.

> **oldfred said:**
> type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Yes that is the one that works

> **oldfred said:**
> Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

Have not tired, but i guess you are right.

> **oldfred said:**
> Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

Thanks, that will be useful - once i can boot Ubuntu.
    
> **oldfred said:**
> So is secure boot on and ubuntu and/or Windows boot from grub menu?
Or do either boot with secure boot off.

The secure boot is off. If i enabel secure boot i get an error messag (before GRUB loads):

Secure Boot Violation
Invalid signature detected. Check secure boot policy in setup.

Edit: after secure boot violation message I have only the possibility to press 'OK' and it then returns to BIOS settings

---

### Post by oldfred on 2013-05-02
It looks like Boot-Repair did the rename of the Windows efi file. But that should only be required with systems that only boot Windows efi file and those that only boot Windows with secure boot on. And then it should have installed the shim (which has Microsoft key) and signed kernels. I think you have to have secure boot on and in Boot-Repair tick the secure boot and it will install those files.

But if you an boot Windows without secure boot, you do not need Ubuntu secure boot files unless you only want system to boot with secure boot. (It does not really add security, it just makes it hard to install any other system). 

So I might un-rename Windows files, so the grub uefi entry just is to the standard Windows file not the renamed one and leave secure boot off.

You want to undo this:
       To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

To undo:
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by ubuntius on 2013-05-02
> **oldfred said:**
> 
       To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

To undo:
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

I tried these steps, but same results. Same GRUB menu.
There is now 2 Ubuntu boot entries in BIOS:
- Boot option #1: Ubuntu (PO: Hitachi HTS545032A7E380)
- Boot option #2: Window Boot Manager (PO: Hitachi HTS545032A7E380)
- Boot option #3: Ubuntu (PO: Hitachi HTS545032A7E380)

I cannot boot ubuntu from usb when SecureBoot is enabled?

---

### Post by oldfred on 2013-05-02
The UEFI menu should give a choice to boot Ubuntu with secure boot on from flash drive. It has the signed kernel and should work.

From Ubuntu and 13.04 should also be the same as it is newer:
 As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

If you unticked the rename, does Windows boot from Windows UEFI entry, or are you still geting grub menu. Do either of the  Ubuntu entries work?
Then try again with secure boot off?

(I really do not know, but the main reason is that every vendor and even different models by vendor behave differently. While systems may be similar exact procedures for every system not available.)

---

### Post by ubuntius on 2013-05-07
Hi Oldfred, thanks for your patience - i've been busy the last 3 days.

> **oldfred said:**
> If you unticked the rename, does Windows boot from Windows UEFI entry, or are you still geting grub menu. Do either of the  Ubuntu entries work?
Then try again with secure boot off?


I've tried the above with no result - I get the GRUB menu every time and none of the Ubuntu entries work.

I still don't understand why I can't boot in SecureBoot mode - when I boot Ubuntu from USB I get no entry for SecureBoot?

Thanks again for your help (and patience)

---

### Post by oldfred on 2013-05-07
When you say none of the Ubuntu entries work, what happens? Black screen. Then you may need nomodeset or other boot parameter(s) on linux line in grub menu. Press e scroll down to linux line, and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

    
If you have Intel you may need to set video mode to your exact screen size. Instead of nomodeset use something like this example but your monitor. 
       Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60

---

