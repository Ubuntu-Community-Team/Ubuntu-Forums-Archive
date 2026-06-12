---
title: "GRUB goes into a loop on chosing windows"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by harsha_vardhan on 2014-08-07
Hello,
Firstly I am new to the forums. So sorry if I violate any rules.

I have installed Ubuntu 14.04 alongside Windows 8.1 on my laptop ( HP Envy 15-j133tx ). It was running smoothly for quite sometime and I could boot into both the OS. But today when I tried to boot into Windows from GRUB it would not boot. Instead the screen would go blank and I would see the GRUB menu again.

So I have seen a couple of threads online which said to install the software 'boot-repair' and running it would solve the problem. The thread in particular was this one [http://askubuntu.com/questions/133725/cant-boot-windows-7-after-installing-ubuntu-12-04-lts](http://askubuntu.com/questions/133725/cant-boot-windows-7-after-installing-ubuntu-12-04-lts). I have run it but it made no change. At the end it gave an error saying the following:

[QUOTE]An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/7978454/](http://paste.ubuntu.com/7978454/)

(removed boot report, see link already posted) or use code tags if long text output.

---

### Post by oldfred on 2014-08-07
Removed very long boot report, you have link and that is all that is required.
Also if posting longer text or terminal output please use code tags. Easy to add with advanced editor with # icon.

You do show grub in gpt's protective MBR for BIOS boot but have UEFI and should only boot in UEFI mode.

Grub did reinstall correctly, exit code 0 is no error.

 Reinstall the GRUB of sda7 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

Boot-Repair has not been updated for 14.04, so it dumps too much grub detail now and may be looking for grub-efi which is now grub-efi-amd64. I think they renamed it now as later they plan a 32 bit UEFI version.
So Boot-Repair may be saying an error, but there is not one.

Did you update Windows 8 to 8.1, I think that was required.

But 8.1 resets UEFI to make itself first in boot order.
And if you had run Boot-Repair before and its "buggy" UEFI fix that renamed the Windows efi file to be grub, and you booted the backup. But then a Windows update refreshed the Windows efi file.

HP has modified its UEFI to only boot Windows, so some work around is required. I now do not like Boot-Repair's rename of the Windows file as you get into the conflicts with Windows.
But you can rename bootx64.efi or add grub/shim to BCD, or use rEFInd. 
Some of these alternatives work better on some systems.

      
 [http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
**a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
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

   **F:** Disable Windows in UEFI and only boot from rEFInd or grub. If Windows is #1

 sudo efibootmgr -A -b 0001

     
Some users who renamed files manually:

 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try differnet USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by yancek on 2014-08-07
Were you using GPT/UEFI mode to boot?  I see an EFI partition (sda2) but also see that Grub is installed in the master boot record.  At the very top of the Boot Repair page you can see a comment that it is looking for core.img at a particular location and it is not there.  Did you do any updates on Ubuntu?  I don't use UEFI but someone should come along to help.

---

### Post by harsha_vardhan on 2014-08-08
Thanks guys for your replies. I have not tried much of the methods specified as I am new to this EFI stuff, and am afraid that I might mess up something and even Ubuntu might not work.

I have now completely shifted to Ubuntu :)

Thanks again guys for your prompt responses!

---

