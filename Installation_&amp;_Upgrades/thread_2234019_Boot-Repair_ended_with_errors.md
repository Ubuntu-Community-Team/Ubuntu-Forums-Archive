---
title: "Boot-Repair ended with errors"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by primogenito2 on 2014-07-12
Hi,
I've succesfully installed Ubuntu 14.04 LTS on a laptop PackardBell EasyNote LE together with the pre-installed Windows 8, the idea is to have double booting.  Here the Ubuntu details:
    [ATTACH=CONFIG]254654[/ATTACH]

Problem is that PC starts per default always with Windows 8.
  In order to be able to boot with Ubuntu, it is needed to press <F12> right after power up in order to call the booting alternatives: Windows or Ubuntu or CD or USB (if attached).  Once Ubuntu is selected, then it comes the Grub menu, where once again Ubuntu and Windows options are given.

After using Boot Repair it ended with errors, indicating following URL:[INDENT][http://paste.ubuntu.com/7782232/](http://paste.ubuntu.com/7782232/)
[/INDENT]
and booting continues to be always Windows 8, for Ubuntu <F12> must be pressed at restart or power up.

I would prefer to have the PC starting like the good old days where Grub menu came at start up and, if nothing is entered, PC boots in Ubuntu.

Support and/or suggestions to solve the mater are most welcomed.
Thanks

---

### Post by oldfred on 2014-07-12
Boot-Repair is picking up some minor error somewhere, but it does say it reinstalled grub correctly as exit code is 0.
grub-install /dev/sda: exit code of grub-install /dev/sda:0
And it shows ubuntu as boot option.
> BootOrder: 0002,0003,0000,0001,0004
Boot0000* HDD0:
Boot0001* HDD0:
Boot0003* Windows Boot Manager
Boot0004* ATAPI CDROM: MATSHITA DVD-RAM UJ8E1
Boot0002* ubuntu,BootCurrent: 0004
Timeout: 2 seconds

Have you tried with secure boot both on and off?

Some UEFI systems have been modified by vendor to only boot the entry with Windows in the description. There are several work arounds.

       [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
**a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry.
**a2:**(this is the same as what Boot-Repair does in B:. 
Rename /efi/Microsoft/Boot/bootmgfw.efi and copy grub or shim into /efi/Microsoft/Boot and name it bootmgfw.efi  Then boot Windows entry to boot to grub menu. You have to manually add a grub menu entry to boot renamed Windows efi file. Grub2's os-prober entry boots bootmgfw.efi entry which is now just grub, so it will not work.

   Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu  with bkpbootmgr.efi entry
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmgfw.efi will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)
Now has a ppa to make it easy to install:
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

### Post by primogenito2 on 2014-07-23
Thanks a lot, very complete answer, now my problem is solved.  
 
 Just for my own documentation in case I would need to repeat the process later on (some forced Windows and/or Grub upgrade/update which revert my manual changes) or in case some one are interested in a detailed description, here what I did:

 0) backup entire efi partition
1) rename /efi/boot/bootx64.efi as /efi/boot/bootx64.efi.org
2) copy /efi/ubuntu/grubx64.efi as /efi/boot/ bootx64.efi
3) rename /efi/Microsoft/Boot/bootmgfw.efi as /efi/Microsoft/Boot/bootmgfw_org.efi
4) copy /efi/ubuntu/grubx64.efi as /efi/Microsoft/Boot/bootmgfw.efi
5) from the file /boot/grub/grub.cfg copy the section corresponding to Windows making with it a new file under /etc/grub.d
6) edit the new file changing the original 'chainloader /EFI/Microsoft/Boot/bootmgfw.efi' into 'chainloader /EFI/Microsoft/Boot/bootmgfw_org.efi'[INDENT]Note: keep in mind that $ is a reserved character, so \ needs to be inserted before in order to have it properly transferred into the cfg file
[/INDENT]
 7) remove executable attribute to original Windows script (30_os-prober in my case)
8) set executable attribute to the 'faked' grub script for Windows boot
9) run 'update-grub' and verify that the new generated /boot/grub/grub.cfg is equal to the original one exception made of the revised filename 'bootmgfw_org.efi' for Windows boot.[INDENT]Note: for steps 5 onwards I got good basis from:
[/INDENT]
[INDENT=2][GRUB 2 bootloader - Full tutorial]("http://www.dedoimedo.com/computers/grub-2.html")
[/INDENT]
[INDENT=2][GNU GRUB Manual]("http://www.gnu.org/software/grub/manual/grub.html") 
[/INDENT]
 
 Once more, Thanks!

 P.S.: Just a note about secure Boot on/off: couldn't try.  I remember to have deactivated it more than a year ago, however somewhere later on I set inadvertently a password and now I can't enter any longer to UEFI settings.  Do you know by chance how to reset that password?

---

### Post by oldfred on 2014-07-23
You should only have to do one rename or the other.
Renaming Windows file may evenually break as a Windows  update its file which of course still has original name. But grub entry to older version of Windows efi file will be outdated and not work.
Best to also have a Windows 8 repair flash drive.

Can you directly boot hard drive which should be the renamed bootx64.efi? Then you would not have to rename the Windows file.

But if you have it working that is great.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)


 We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $20 or $40  for the download. So make one yourself before you have to pay to get one.
[http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/](http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/)
Make your own Windows recoveryCD/repair: (free)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

