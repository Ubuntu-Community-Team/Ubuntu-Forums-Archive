---
title: "Stuck on dual boot configuration 14.04 and Windows 8.1 on HP Envy"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by robertj20112 on 2014-12-22
Okay, I've installed 14.04 LTS with EFI and Secure Boot enabled.  My problem is that the HP automated boot process ignores the presence of Ubuntu and boots directly into Windows.  The only way I can boot into Ubuntu is to intercept the boot processby pressing the Escape key immediately, selecting Boot Device options (F9). choosing "Boot from EFI File", then pressing Enter on the next page (a description of the hard drive), choose EFI from the next screen, select "<ubuntu>" from the subsequent list, the select "shimx64.efi" from the next screen, which gives me the Grub list (without, I might add, any reference to Windows!)  So, while it works, it is a laborious process at best.  Have tried to follow the following post from an HP help forum:

[INDENT]So, until HP releases an updated UEFI that allows turning this "feature" off or rearranging boot options through the F10 UEFI setup, this is what you can do to get dual boot with the least amount of hackiness:
 In Windows, mount the UEFI partition (mountvol S: /S mounts it as the S: drive) and copy the file \EFI\Microsoft\Boot\bootmgfw.efi to use some other name (for example, I copied it to "\EFI\Microsoft\Boot\bootmgfw.efi~", but you can change the name to anything else).
    In the Windows command prompt, update the Windows UEFI entry to point to the new name: bcdedit /set {bootmgr} path \EFI\Microsoft\Boot\bootmgfw.efi~ (adapt to your set name accordingly).
    Optionally, change the name of the Windows boot loader so that you would be certain that it points to the new file location: bcdedit /set {bootmgr} description "Fixed Windows path"
    Install the other OS. In my case the bootloader was installed into \EFI\opensuse\grubx64.efi.
    Delete the two files, \EFI\Microsoft\Boot\bootmgfw.efi and \EFI\Boot\bootx64.efi.
    Use efibootmgr to delete the "OS boot Manager" entry: sudo efibootmgr -b 0000 -B
    Set the new OS bootloader to be the default bootloader by using efibootmgr with the -o option. In my case, I had an entry called "opensuse" in slot Boot0001 and the updated path Windows entry in slot Boot0002, so I had to do sudo efibootmgr -o 0001,0002
    Update GRUB to point the Windows entry to your renamed file (you'll have to create a new file in /etc/grub.d and rerun grub-mkconfig).[/INDENT]

Was able to do everything as posted except "Delete OS boot Manager", because there is no entry for that item when I run efibootmgr in Ubuntu terminal.  I did reorder the boot order using efibootmgr so that Ubuntu was first and Windows was second, but the HP OS boot Manager changes it back!  

I have attached a copy of a session where I changed the boot order.  Once I reboot the computer (and it goes directly to windows 8) the file has been changed back to the first version in the attachment.  Sure would like some help.  Sorry for the length of the post.  Let me know what further information would be required to sort this out.  Thanks in advance.

Sam Johnson
[ATTACH]258737[/ATTACH]

---

### Post by oldfred on 2014-12-22
Most with HP seem to have success copying grub or shim (not sure what OpenSuse has) to \EFI\Boot, backing up bootx64.efi which is the hard drive boot entry, and rename grub to bootx64.efi. Then boot the hard drive entry in HP's UEFI. If /EFI/Boot does not exist, you may have to add it, and then add entry into UEFI with efibootmgr. Then select that entry as first.

Some also like rEFInd, or in Windows set an entry bcdedit. Windows syncs its BCD with UEFI regularly.

If you end up copying grub, then with a major grub update you will have to copy it again or get into version difference errors.
And if you rename the Windows efi file bootmgfw.efi, Windows updates will regularly overwrite it with  a new 
Windows copy, so you have to redo it regularly.

Some of the work arounds. Some better than others depending on configuration and brand/model system.
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Other HP where they copied files:

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

---

### Post by robertj20112 on 2014-12-23
WOW!  What a comprehensive reply!  Thanks, oldfred.  I've tried to understand the various approaches in the links above, and my conclusion is there is no elegant, permanent solution as long as the boot process goes through the HP OS boot manager.  Have I missed something critical?

---

### Post by oldfred on 2014-12-23
Only if not dual booting with Windows. Then you can use the option to rename grub/shim in UEFI to read Windows, but really boot the /EFI/ubuntu/grubx64.efi.
       
 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

The other solution that has worked for some, but I have not used rEFInd, is rEFInd. It started with Mac as update to refit, which is not maintained anymore, but works on PC just as well.
Some more links:
 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[URL="https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd"]https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd
[/URL]https://wiki.archlinux.org/index.php/REFInd/

This was in link above to all the alternatives:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

