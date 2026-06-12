---
title: "Suddenly UEFI dual boot shows &quot;grub minimal bash-like...&quot;"
date: 2014-07-14
forum: Installation &amp; Upgrades
---

### Post by Ev1L on 2014-07-14
Up to a couple of days ago I could boot mint17 (yes, yes, I know, this is ubuntu, but the problem is the same for both :) ) and win8 from grub, then suddenly win8 started booting automatically, so i booted a live mint and renamed Microsoft EFI folder.
Now no matter how I rename EFI folders I get only to:

```
Minimal bash-like line editing is supported.

grub>
```

I currently removed completely the EFI folder (Boot, Microsoft, ubuntu in there) and still nothing changed.

Where is that grub supposed to be?
I know that Sony Vaio Pro 13 might be messing up with EFI, but since it was working...

---

### Post by ubfan1 on 2014-07-14
You must have installed in both UEFI and legacy mode, since apparently you have Grub in the MBR, which your machine must fall back to when no EFI boot files are found.  What disks/partitions does Grub see?  You can use ls (hd<TAB> or "set root=(hd<TAB>  to get a device /file choice and see if you Ubuntu file are still readable.  Anyway, restore the EFI files, you will want to be in UEFI mode for dual boot with Windows.  The boot order does seem to get reordered all the time, with Windows putting itself first, but running efibootmgr from a live media should allow you to fix that.

---

### Post by Ev1L on 2014-07-14
thanks, the partitions were not changed, both systems UEFI and visible.
i could start mint pointing to its boot manually from that grub console.
eventually i found the old solution for my sony crap (see [http://forums.linuxmint.com/viewtopic.php?f=60&t=166161):](http://forums.linuxmint.com/viewtopic.php?f=60&t=166161):)
sudo cp /{efimount}/EFI/Microsoft/Boot/bootmgfw.efi /{efimount}/EFI/Microsoft/bootmgfw.efi
then updating grub to restore win8.

unfortunately, after I boot to windows once, i lose grub and it boots only in windows.
doing the same file replacement seems not enough, and i am afraid i need to go again renaming the microsoft folder so it won't find windows, and then again restoring as above.
there must be a better way...

---

### Post by oldfred on 2014-07-14
Windows likes to make itself first. And Sony's only boot Windows UEFI entry.

Your rename of Windows efi file is what Boot-Repair does, but then you cannot directly boot Windows from UEFI menu and updates in Windows overwrite the bootmfgw.efi file with new Windows version. 

Probably better to rename bootx64.efi or try some of the other alternatives.

 [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
**a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry.
**a2:**(this is the same as what Boot-Repair does in B:. 
Rename /efi/Microsoft/Boot/bootmgfw.efi and copy grub or shim into /efi/Microsoft/Boot and name it bootmfgw.efi  Then boot Windows entry to boot to grub menu. You have to manually add a grub menu entry to boot renamed Windows efi file. Grub2's os-prober entry boots bootmfgw.efi entry which is now just grub, so it will not work.

   Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu  with bkpbootmgr.efi entry
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)
Now has a ppa to make it easy to install:
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

### Post by Ev1L on 2014-07-15
Thanks for the long list :)

Boot-repair didn't work for me unfortunately. Although I did the manual file replacement that it was supposed to do, only the manual procedure worked for me.

What I understood about the Sony tyranny, is that when it cannot find a valid bootable EFI, it restores its Microsoft one (and the same happens with win updates).
So, if I replace that with a Ubuntu one, it boots to grub, and it should stay because it is valid.
However, I don't understand why:
1 - when I renamed or removed the Microsoft folder (and all the others), it started up to an empty grub rather than recreating Microsoft as expected
2 - why now after a simple Windows boot, it keeps booting it and even replacing the bootmfgw.efi doesn't do the trick anymore.

FYI (and for my future self-reference :) ):
A: tried both, they were the only things that worked, except right now
B: didn't work, with or without defaults and combining different settings
C: didn't work
D: I guess I didn't try this, but now I remember reading the some manufacturers are so stupid to hardcode that name
E: didn't work, maybe it would work in combination with one of the above, because with refind I was still seeing the empty grub console

---

### Post by oldfred on 2014-07-15
I think Sony UEFI is not restoring the efi files, but the UEFI NVRAM entry to boot the Windows entry.
But if you boot into Windows it may restore the Windows efi file.
So I think the rename of bootx64.efi works the best of the alternatives.

I think Windows still has a offical policy of until only Windows can be used they cannot ship the product. 
(Actual court case from years ago proved that then with DOS and competing products).

---

### Post by Ev1L on 2014-07-15
thanks, it makes sense :)

so if i understood correctly, with renaming you mean replace all bootmfgw.efi with the (renamed) bootx64.efi.
this should not be replaced by windows until some windows update does that, correct?

---

### Post by oldfred on 2014-07-15
The bootmfgw.efi is the Windows boot file in the Microsoft folder.
The bootx64.efi is a shell file which both Windows or Ubuntu may provide to get into UEFI in the /efi/Boot folder. Changing that file allows you to still directly boot Windows with its own bootmfgw.efi file from UEFI menu, and usually is not overwritten as often as the Windows boot file on Windows updates.

Folders:
 /EFI/Boot
/EFI/Microsoft
/EFI/ubuntu

---

### Post by Ev1L on 2014-07-16
i might still not seeing the whole picture (thanks for the patience).
I replaced all bootmfgw.efi with the bootx64.efi from ubuntu.
nevertheless it boots straight to windows. is it because of UEFI NVRAM is set with the windows loader ignoring what is in the EFI folder? in that case how do I reset it?
manipulating with efibootmgr didn't help.
perhaps with bcdedit...

Update:
C:\Windows\system32>bcdedit
The boot configuration data store could not be opened.
The system cannot find the file specified.

---

### Post by oldfred on 2014-07-16
Windows needs a bootmfgw.efi to boot.
You should be copying grubx64.efi or shimx64.efi into /efi/boot and rename one or the other to bootx64.efi.
Better not to rename or change bootmfgw.efi or any other files in /efi/Microsoft.

If now BCD issues those cannot be fixed from Linux, you need your Windows repair flash drive or other third party Windows repair tools.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

      
 BCDboot Command-Line Options Windows Vista/7/8 recreates boot files.
[http://technet.microsoft.com/en-GB/library/hh824874.aspx](http://technet.microsoft.com/en-GB/library/hh824874.aspx)

---

### Post by Ev1L on 2014-07-22
I just realized that the problem appears (at least) when Restart Mint (shutdown + boot is ok instead).
With Reboot, it goes in the Vaio screen for too long, apparently cannot find what to load, then flashes black, goes again in Vaio screen and ends up in some sony screen asking to change the boot options or recover windows.
Pulling the plug and starting again goes straight to Windows.

---

