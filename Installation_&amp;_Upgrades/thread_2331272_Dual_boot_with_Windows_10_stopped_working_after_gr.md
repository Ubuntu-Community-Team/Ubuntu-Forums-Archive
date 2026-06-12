---
title: "Dual boot with Windows 10 stopped working after grub update"
date: 2016-07-20
forum: Installation &amp; Upgrades
---

### Post by onuralparslan on 2016-07-20
I have kubuntu and Windows 10 on separate drives. After updating grub, I cannot enter Windows 10 anymore. When I click on "Windows boot manager" option in grub menu, the grup menu reappears instead of entering Windows boot. When I click "windows boot uefi loader" option, the windows boost screen with black background and blue windows logo appears but it stops there and does not show the login screen. I rebooted by pressing power button and tried "windows boot uefi loader" option again. This time windows boot screen said entering automatic repair but then failed with a blue screen saying wdf_violation. Does it mean that grub deleted my windows boot manager? I tried boot-repair with default options, but it did not work. The bootinfo summary is available at [http://paste2.org/hLMML3WZ](http://paste2.org/hLMML3WZ)

---

### Post by yancek on 2016-07-20
Did you try setting the 250GB disk (sda) with Ubuntu on it to first boot priority in the BIOS as suggested.

I wouldn't expect an update-grub to cause problems like this if it was working correctly.  What exactly was the reason for updating grub?
Your windows drive (sdb) has an EFI partition with both windows efi files and Ubuntu efi files.   That's correct but the problem is that you have also installed windows code in the MBR of that same disk and you have a second EFI partition on the other disk.   You only need on EFI partition regardless of the number of drives and having code in the MBR with an EFI computer causes problems.  You might take a look at the Ubuntu documentation below on dual booting with UEFI.  I don't use UEFI myself but there are a number of members here who are very knowledgeable so you'll have to wait for their response.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-07-20
Did you change drive order (SATA port order)?
You show both Windows on Ubuntu in ESP on sdb, but only Windows on ESP in sda. But grub only installs to the ESP on sda.

A Google search says your wdf violation is from a hardware change in Windows (Drive order?). And you left Windows in its fast startup or always on hibernation.
You may also have UEFI in fast boot? Better to have that off whenever you have hardware changes, as it can be more difficult to get into UEFI to change settings.

You only have UEFI installs, but now show a Windows BIOS boot loader in the gpt protective MBR. That might attempt to boot in BIOS mode but would definitely give errors as it cannot work. Do not boot in BIOS mode, only UEFI.

Grub will only boot working Windows, or Windows that is not hibernated(fast start up) nor needs chkdsk. With UEFI you should be able to directly boot Windows with one time boot key like f10 or f12. You may need f8 to get into Windows repair console also.

You also show a lot of old kernels. Is this system an upgrade? Old kernels may then not be in dpkg to remove the way they should be.

      [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels)

Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)

---

### Post by onuralparslan on 2016-07-20
Problem started after upgrading to latest version of kubuntu. Then I tried boot-repair, which may have worsened the condition.
I uninstalled old kernels now, but the problem is not solved.
Clicking F10 gives the BIOS setup utility and clicking F12 tries to boot from network controller
From the BIOS menu I entered boot order menu. It gave me these options
UEFI Boot Source
-Windows Boot Manager
-UEFI: MTFDDAK256MAM-1K1
Legacy Boot Sources
-Hard Drive
--SATA0
--SATA!
-Network Controller

I tried both Windows Boot Manager and UEFI: MTFDDAK256MAM-1K1, but they gave the same menu and they could not load Windows 10
I cannot login to windows and also windows repair is crashing with wdf violation, so I cannot check or disable Fast Startup

How can I solve this problem? Maybe boot repair with some advanced configuration can fix it?

---

### Post by oldfred on 2016-07-20
Boot-Repair is primarily for Linux issues. 
It can only do very minor issue fixes with Windows.

You should have a current version repair flash drive for every operating system you have installed, but many do not make the Windows one.
If you have access to another Windows system, you can make a repair flash drive from that, just has to be same 32 or 64 bit.
       [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[URL="http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive"]http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive
[/URL]
 f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 

For Windows repairs you may do better in a Windows forum.

[URL="http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive"]
[/URL]

---

