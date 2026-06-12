---
title: "Unable to get bootloader up"
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by topaz3 on 2014-03-03
Hello all,

I am trying to figure out how to recover after recently upgrading my computer to Windows 8.1. 
Previously, I had patitioned my harddrive such that both Ubuntu 12.04 and Windows 8 can be used. I installed Grub using boot-repair, and everything worked fine.
I upgraded my computer to Win 8.1 and that broke my bootloader.
So I used a Ubuntu Live CD to boot into ubuntu and use boot-repair to install Grub again. 
But now, nothing I tried works. 
Every time I turn the computer on, I get a message that it is unable to find a device to boot.

My output of the file system is here: [http://paste.ubuntu.com/7026134](http://paste.ubuntu.com/7026134).

My windows 8.1 is loaded in UEFI mode. I have tried to load the bootloader in both legacy and efi mode.
I have tried disabling and enabling the secureboot, nothing seems to work.

If anyone has a suggestion, I would really appreciate it.

Thanks,

---

### Post by topaz3 on 2014-03-03
Update:
I reinstalled Ubuntu 12.04 with UEFI mode and SecureBoot enabled.
The message I get is "No boot device avaialble"

---

### Post by joao2 on 2014-03-03
I guess I have a similar problem in my thread.
Really, this UEFI is cracking my head.
Sorry for not being able to help, but I will also follow yout thread closely. 
Hopefully some *guru* might be able to find a solution.
:)

---

### Post by oldfred on 2014-03-03
Not sure now what changes you now have done.

But Windows 8 likes to keep making itself the default boot loader.
Your install of Ubuntu was not the secure boot version, so you have to make sure you have secure boot off.
Your Windows is UEFI, so you do not want any BIOS boot.

Grub does have a bug and will not boot Windows 8 from grub menu if secure boot is on. But I do not think you would get to that point unless you had Boot-Repair reinstall the secure boot version of Ubuntu grub2 & kernels.

It looks like you had run the "buggy" UEFI fix in Boot-Repair. That is for those computers that only boot Windows.
But it renames the Windows boot file to be grub or shim to directly boot grub using Windows names so UEFI thinks it is booting Windows. But then you only can boot Windows renamed/backedup efi file from grub.  But that may now be the older version of Windows efi file and Windows overwrote the Windows file that boot repair had made to be shim/grub.

And now with version differences I would not suggest using Boot-Repair to undo the change. You probably should have undone the rename before upgrading Windows and then redoing after the upgrade to keep files in sync.

Can you boot the ubuntu entry in UEFI menu with secure boot off in UEFI, and fast boot off in Windows?
This is from your UEFI, but some vendors modify it to not let you use anything but Windows.

BootOrder: 0003,0002,0001,0000
Boot0000  P1: PLDS DVD+/-RW DH-16AES
Boot0001  P0: ST1000DM003-1CH162
Boot0002* UEFI: PLDS DVD+/-RW DH-16AES
Boot0003* [COLOR=#ff0000]ubuntu[/COLOR]

---

### Post by ubfan1 on 2014-03-03
Check your Windows power option settings again, the 8.1 upgrade resets the "fast startup" option, which basically short circuits the whole boot process.  Turn that option off again and hopefully things will be working.

---

### Post by topaz3 on 2014-03-04
Hello all,

Thank you all for the comments.
[COLOR=#ff0000]
oldFred:
Can you boot the ubuntu entry in UEFI menu with secure boot off in UEFI, and fast boot off in Windows?
This is from your UEFI, but some vendors modify it to not let you use anything but Windows.[/COLOR]

I tried reinstalling Ubuntu with secure boot off and in UEFI mode. However, I can't change the fast boot option because I can't even get into Windows.

[COLOR=#ff0000]ubfan1:
Check your Windows power option settings again, the 8.1 upgrade resets  the "fast startup" option, which basically short circuits the whole boot  process.  Turn that option off again and hopefully things will be  working.[/COLOR]

I can't even get into Windows. Can someone explain how I can boot into Windows? It seems that the files that boot into Windows have been trashed? I see them in the report from boot-repair.
Is there a way to turn off the fast boot option without gettting into Windows? I have checked the BIOS, and I didn't find anything like that.
My system is a Dell XPS8700 by the way, if that helps.

My new file from boot-repair is at [http://paste.ubuntu.com/7031567/](http://paste.ubuntu.com/7031567/)

Thank you all, and waiting for your reply.

---

### Post by oldfred on 2014-03-04
You cannot do most fixes to Windows from Linux. You need Windows repair flash drive.

Did your run the "buggy" UEFI fix from Boot-Repair. That is for those vendors that modify UEFI to only boot Windows. It renames the Windows efi files and makes the original grub/shim, so from Windows UEFI entry you actually boot Windows.
If you can boot ubuntu entry undo rename. If you did the rename after update to 8.1 run this. But if you did it before it may restore the 8.0 version and not work.
       
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Boot-Repair renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

    
But you may need to manually copy this to efi folder, if above fix does not work:
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.
[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)


        Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

But you should be able to boot Windows directly from UEFI menu, and maybe get into its repair. Not sure of details.

---

### Post by topaz3 on 2014-03-08
Hello,

Thanks for the info.
I am getting tired with all of these booting problems.
Would it be easier to install a new hard-drive in the computer, and install linux on that?
So I plan to have a hard drive with Win 8, and another hard drive with ubuntu.
So boot from the linux hard drive, and install grub on the linux HD.
Will GRUB on the ubuntu HD find the windows boot files for booting Windows on the other hard drive,
and will I be able to boot up Windows in this case?

Thanks your help.

---

### Post by oldfred on 2014-03-08
Yes you can use two drives.
Best again if both are UEFI installs and that you create a efi partition on Linux drive. It may normally use the efi partition on the Windows drive.
Not sure we have resolved if your computer is one that only Boots Windows or not.

Other threads with dual boot on two drives.
 **Two Drive UEFI installs**
[http://ubuntuforums.org/showthread.php?t=2192378](http://ubuntuforums.org/showthread.php?t=2192378)
HP Envy 2 drive install i7 & 2 1TB drives
[http://ubuntuforums.org/showthread.php?t=2175877](http://ubuntuforums.org/showthread.php?t=2175877)
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

---

