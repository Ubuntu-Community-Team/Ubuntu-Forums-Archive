---
title: "Win 8.1 and Ubuntu 12.04 dual boot problems"
date: 2013-12-12
forum: Installation &amp; Upgrades
---

### Post by s.boone35223 on 2013-12-12
Current set-up:  Toshiba Satellite C50-ABT3N11, Windows 8.1 64 bit, Ubuntu 12.04, [http://paste.ubuntu.com/6559281](http://paste.ubuntu.com/6559281)

I have run Boot Repair three times to try and resolve a dual boot issue.  The first two times I selected "yes" to rename the Windows EFI settings.  The third time, I selected "do other thing" (see URL above).


The first time I ran boot repair, it seemed to work for a while.  I got to a GRub screen (although it had many more options than necessary).  After going back a forth between Windows 8.1 and Ubuntu 12.04 2-3 times, it stopped working booting directly into Windows. 


I can hold the Shift key down during a reboot to get to what looks like a blue Windows boot screen option (HDD, USB, DVD, etc.)  When I select HDD, it takes me to another blue screen where I can select Windows, ubuntu, or Ubuntu?  Either Ubuntu option appears to hang up and load Ubuntu only after pressing the enter key.


Laslyt, I attempted to reinstall Ubuntu.  While it appeared to reinstall, none of my apps were removed, my password did not change and none of my pics or docs were deleted so it appears that the reinstall did not do anything.

Windows 8.1 does work and Ubuntu 12.04 works too, I just cannot get the dual boot Grub to work correctly.


Any help will be appreciated.

---

### Post by oldfred on 2013-12-12
Can you boot the ubuntu entry from UEFI menu or just Windows entry.
Boot-Repair did the rename that those that can only boot Windows entry. The rename changes the Windows entry to be grub2's shim so UEFI still thinks it is booting Windows but really boots grub. 
As you are configured now both ubuntu entry & Windows entry should give you grub menu and from grub menu you can boot the renamed/backed up Windows efi file.

If you can boot ubuntu entry in UEFI menu then better to undo rename. Windows may overwrite the shim file with a new copy on updates and you will have to fix it periodically. If not renamed and works then you just have to reset in UEFI menu boot order.
 Boot-Repair renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 


I think turning off NIC may prevent network from running. And then updates during install will not work.
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
> Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by s.boone35223 on 2013-12-12
I checked to be sure Win 8.1 Secure Boot was not enabled with an upgrade (still disabled).  I also looked in UEFI and found where Windows is in UEFI mode.  I then went to Ubuntu 12.04 and determined that it is Legacy mode.  From what I have read, it appears that Ubuntu needs to be installed in UEFI mode same as Windows.  Is that correct?

If so, can this be done without reinstalling?  How?  If a reinstallation is required, is UEFI an option from the Ubuntu installer (I don't recall).  I am hesitant to reinstall as I have done so once already and nothing appears to have changed since docs, apps, pics, etc. were still present after the reinstallation process.

Thanks.

---

### Post by oldfred on 2013-12-12
Boot-Repair can convert a BIOS install to UEFI by having you chroot into your system (it tells you how or helps you) and then it uninstalls grub-pc (BIOS) and installs grub-efi (UEFI).

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If Boot-Repair offers to run the rename decline it initially. That is only required for those systems that have "buggy" UEFI that only boot Windows entry in UEFI and will not boot ubuntu entry. We must confirm that you cannot boot ubuntu before trying the rename as it may later have issues when Windows updates the renamed file and you then need Boot-Repair to redo the rename.
Windows also has been known to reset Windows as default in UEFI, but if files are not renamed, you just need to go back into UEFI and set ubuntu as first boot choice.

---

### Post by s.boone35223 on 2013-12-12
I loaded Boot-Repair and selected the following options

Main options
x Reinstall Grub
x Restore EFI backups
x Unhide boot menu

Grub location
x Separate/boot/efi partition = "sda2"

Grub options
x Secure boot
x Purge grub before reinstalling

When I rebooted, it loaded Windows 8.1 directly.  I can still get to the Windows blue screen to specify boot media by holding F12 during boot.  When I select HDD, I am directed to another Windows blue screen with Windows, ubuntu, and Ubuntu choices.  One of the two Ubuntu options does not work.

---

### Post by oldfred on 2013-12-12
Does one of the Ubuntu options get you to a grub menu?

And from Boot-Repair post link to BootInfo report.

---

### Post by s.boone35223 on 2013-12-12
Boot-repair report 

[http://paste.ubuntu.com/6564174](http://paste.ubuntu.com/6564174)

Thank you.

---

### Post by s.boone35223 on 2013-12-12
Grub configuration file below (is this what you were referring to regarding Grub menu)?

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

### Post by oldfred on 2013-12-12
No do you get grub menu. from Ubuntu in UEFI. 

It looks like Boot-Repair already did the rename. So then when you boot the Windows entry from UEFI you also get grub menu.

You can only boot Windows from this entry in grub menu.
 Windows UEFI bkpbootmgfw.efi

      
 It looks like boot repair ran its "buggy" UEFI rename function. I am not sure it is always required, but it is for those UEFI that internally hard code UEFI to only boot the Windows efi file. So Boot-Repair renames the Windows file and makes grub2's shim be the Windows file. The UEFI thinks it is booting Windows but is really booting grub2 and then from grub2 menu you can boot Windows.

   Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.
Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

Is this a new Haswell or 4th gen Intel processor?
Intel helped make a lot of changes to video driver, kernel & others files to work with the new Haswell systems. But that only is in 13.10. They now are working on next gen and some of those improvements will be in 14.04 and may help the the current gen chips work better.

---

### Post by s.boone35223 on 2013-12-12
I am lost.  When I last ran the Boot-Repair, I ticked the "Restore EFI backups" option.

How else can I restore the back-up?

As far as this processor, I am not sure.  I thought is was an I3.

---

### Post by s.boone35223 on 2013-12-12
You say there is a backup of bootmgfw.efi located at C:\Windows\Boot\EFI\bootmgfw.efi.  Where is the renamed filed located?  Can I not rename the file manually using Windows edit?

---

### Post by s.boone35223 on 2013-12-12
I ran the Toshiba Windows 8.1 Startup Repair utility then re-ran Ubuntu Disk-Repair (Recommended Repairs).  The Repair Bootinfo report is located at [http://paste.ubuntu.com/6564481](http://paste.ubuntu.com/6564481).

Nothing has changed in the boot operation.  Windows still boots.  I can only get to Ubuntu by holding F12 during reboot, selecting HDD then Ubuntu then pressing enter once the Ubuntu screen hangs up.

Any ideas how I can restore or rename the bootmgfw.efi file?

---

### Post by oldfred on 2013-12-12
The un-rename must have worked it is not shown.

>  menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root D699-B5F1
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}



The bkpbootmgrw.efi is not shown now.

While f12 gives you an ubuntu boot option, can you in UEFI change to make ubuntu boot option the first choice? Similar to what others have posted.

---

### Post by ubfan1 on 2013-12-13
The efi boot menu entries, Ubuntu and ubuntu, may be for the shim.efi (for secure boot enabled) and for grubx64.efi (without secure boot).  I looked in your pastebin but didn't see the output of running sudo efibootmgr -v   which lists the entries and what they actually run.  I have a Toshiba S855 which experiences bug #1091464, which prevents grub from running windows, so I have to use the efi menu to select Windows if Ubuntu is the default.  You should be able to change the default OS which boot at powerup with efibootmgr, then you can select windows with the efi menu when necessary.

---

