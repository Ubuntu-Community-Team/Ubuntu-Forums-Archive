---
title: "Cannot boot Windows 7 using GRUB"
date: 2014-10-24
forum: Installation &amp; Upgrades
---

### Post by Dragon2012 on 2014-10-24
Hi Guys,
I've checked forums and have found similar problems to mine, but not exatcly the same.
I've had Ubuntu 12 and Windows 7 installed on my Lenovo Y580 since a long time, but few days ago, I think after some electricity loss I noticed that GRUB is not showing anymore and Win7 is starting automatically. As so today I've booted Boot-Repair on USB which repaired my GRUB. After repairing Boot-Repair gave me that link to output of the whole process: [http://paste.ubuntu.com/8661155/](http://paste.ubuntu.com/8661155/) 
Now I can see the GRUB menu, I can normally logon with Ubuntu (typing from it now), but when I'm trying to choose Windows7 boot I'm getting the following error message:
```
error: no such device: 5411-2310
error: file not found

Press any key to continue...
```

I've tried executing `sudo update-grub`, but it did not help.

I would be very grateful for any help from you how can I get access to Win7 back. Thank you in advance!

EDIT:
I've also checked using Grub Customizer what is the value of Windows 7 entry as a GRUB option:
```
search --fs-uuid --no-floppy --set=root 5411-2310
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi

```

---

### Post by yancek on 2014-10-24
You have an EFI partition with the EFI boot files for both Ubuntu and windows but you also have Grub in the MBR of both drives.  As I understand it, with UEFI you should not have anything in the MBR.  The no such device error is pointing to sda1 which is your EFI partition so maybe you don't have it set to boot EFI in the BIOS.  I'm pretty sure the problem is related to this but I don't use EFI so you'll have to wait for someone else who is more familiar to give suggestions.

---

### Post by oldfred on 2014-10-24
What computer & model is this.

You must have installed Ubuntu in BIOS mode on sdb which is a MBR(msdos) drive. And the grub in the MBR has not been overwritten.
And you have Windows booting in UEFI mode from sda which is gpt partitioned.

With that configuration you had to only boot from UEFI/BIOS menu or f12 (or other depending on vendor) one time boot menu. UEFI and BIOS are not really compatible, so once you start booting in one mode you cannot switch to the other mode. Or grub menu does not work.

I used to think your configuration was not even possible but Boot-Repair has done the same to other systems and it does boot. Officially you are supposed to have gpt partitioning for UEFI boot. But you only have gpt on sda. Boot-Repair then added an UEFI boot for Ubuntu the efi partition on sda, but it boots the install on sdb. Then grub should also let you boot Windows in UEFI mode.

Before we only knew Boot-Repair's fix of renaming Windows efi boot file and making it grub. Some vendors modified UEFI to only boot an entry with Windows in the name. There now are several other work arounds which for most systems may work better. Also back then grub2's os-prober would not find Windows in UEFI mode and only the Boot-Repair entry would work.

This is the real Windows efi boot file, but renamed with bkp....
 /EFI/Microsoft/Boot/bkpbootmgfw.efi
And this now is really grub2's efi file:

 /EFI/Microsoft/Boot/bootmgfw.efi

So if you choose to boot Windows in UEFI menu it really boots grub. And then only from grub menu can you boot the bkpbootmgfw.efi file to actually boot Windows. 
Generally better not to rename Windows file as Windows updates will overwrite it and revert to only booting Windows. 

Can you boot ubuntu entry in UEFI menu? Or only the Windows entry in UEFI menu? If you can boot ubuntu, then you do not need the rename and can revert Windows to its own name and directly boot it from UEFI menu.

Long term you should think about backing up sdb, and converting it to gpt partitioning.

You also have updated 12.04 to one of the point releases.


 Confused about HWE - Hardware Enablement Stack 12.04
[http://ubuntuforums.org/showthread.php?t=2238876](http://ubuntuforums.org/showthread.php?t=2238876)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
12.04.4 point release will ship with a newer 3.11 Ubuntu kernel  from Ubuntu 13.10 Saucy
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
[http://releases.ubuntu.com/12.04.2/](http://releases.ubuntu.com/12.04.2/)
Release notes 12.04.2 Feb 2013
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel)
Info on updates to LTS Enablement stacks
[http://ubuntuforums.org/showthread.php?t=2234693&p=13074774#post13074774](http://ubuntuforums.org/showthread.php?t=2234693&p=13074774#post13074774)
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by Dragon2012 on 2014-10-25
Thank you for answering.
I mentioned at the beginning - it is Lenovo Y580.
By UEFI menu you mean the GRUB menu (purple one, by defult) ? So in that menu I can only boot Ubuntu, booting Windows I get the error message mentioned.
I don't quite understand what should I do now. The most important for me at the moment is to get the access to Windows 7. 
You mentioned > If you can boot ubuntu, then you do not need the rename and can revert  Windows to its own name and directly boot it from UEFI menu. so I changed it using 'e' button when GRUB menu appeares and changed it for: 
```

setparams 'Windows 7 Professional'
search --fs-uuid --no-floppy --set=root 5411-2310
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
```

but it is still not working... :(. I get the same error message.
Maybe I should try to use Boot-Repair again running on Ubuntu ? I just need to have my access to Windows 7 back as soon as possible. Thank you for your help!!

---

### Post by oldfred on 2014-10-25
That is grub menu.

Are you consistently booting in UEFI mode? You may have changed to BIOS mode and that would cause this type of issue.
You do still have a grub in the MBR of sdb that might boot Ubuntu in BIOS mode, but then you could not boot Windows. BIOS & UEFI are not compatible. You have to boot in UEFI mode for grub menu to work to boot Windows in UEFI mode.

And it should boot the bkpbootmfgw.efi which you have in your menu as that should be the Windows efi file.
The bootmgfw.efi should be a copy of grubx64.efi renamed. So trying to boot the bootmgfw.efi just boots grub menu again.

But if still having Windows boot issues, it probably then is just Windows. Grub really only boots a working Windows. If you leave it hibernated or it needs repairs you cannot fix that from Linux.

Did you make a Windows repair CD or Flash drive. It is free and you can easily do it when Windows works. But they charge $20 to $40 to download one when Windows does not work.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

            We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $20 or $40  for the download. So make one yourself before you have to pay to get one.
[http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/](http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/)

Can you boot ubuntu entry directly from UEFI menu? 
If so we will undo the renaming and you can directly boot Windows from UEFI. And if issues f8 may work to run repairs from its own repair console. But still best to have a Windows repair CD or flash drive.


            Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)

             [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
[http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212](http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212)

---

### Post by Dragon2012 on 2014-10-25
I've checked is BIOS - I have: UEFI Boot - Enabled. When I disable it, and reboot my PC, I do not see any boot or system choosing screen, it's just some error and "grub rescue >".
So UEFI Boot is Enabled. I turn on the PC, I have GRUB menu and I can boot Ubuntu with no problems. I'm just typing from Ubuntu now. But when I try to boot Windows 7, I get the error mentioned in the 1st post.
I don't have Windows Recovery CD.
The problem is I cannot access Windows in any way. I really need to access it and would prefer not to order any recovery CDs... So what could I do now to access Windows 7 somehow? Should I change something? If yes, where and how to do that? I'm not professional Linux user :).

As I can boot Ubuntu from UEFI (GRUB), you wrote:
> If so we will undo the renaming and you can directly boot Windows from UEFI
how can I do that ?

---

### Post by oldfred on 2014-10-25
Make a backup of the efi partition.
I am now not 100% sure of which efi file is which. 

Use Boot-Repair and undo the renaming.
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

That should make the bootmgfw.efi be the 'real' Windows efi boot file. System may default boot to Windows if it is ok. If not then you need Windows repairs that can only be done from Windows repair console. Some third party tools may work and limited versions of those are free.

You should in UEFI menu have entries for Windows and ubuntu as well as the hard drive or other devices.
One time boot key should also give UEFI choices, but may include the BIOS entry also which does not work.

Not sure if Windows 7 also has this but I would expect so:
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

### Post by Dragon2012 on 2014-10-25
It helped! Running Boot-Repair with option "Restore EFI backups" and during installation cancelling name changing helped. Now I have GRUB and can boot Win7 and Ubuntu :). Thank you soo much!

---

### Post by oldfred on 2014-10-25
Glad that worked. :)

---

