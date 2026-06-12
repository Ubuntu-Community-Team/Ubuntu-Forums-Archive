---
title: "No bootable device available!!! Dual Boot EFI"
date: 2013-09-14
forum: Installation &amp; Upgrades
---

### Post by B34N on 2013-09-14
I'm trying to Dual Boot 13.04 64-bit with Windows 8 Preinstalled on a Dell XPS 8500

Ubuntu 13.04 64-bit installed fine but upon rebooting it went right into Ubuntu and never gave me the option to boot into Windows 8. I did not need to change anything in the BIOS to get Ubuntu to install other than change the boot order of the devices so that I could boot from DVD. I did not use Ubuntu to resize my existing Windows 8 partition. Instead I used the tool within Windows 8.

After successfully booting into Ubuntu, I confirmed that it was installed in EFI mode.

I followed troubleshooting instructions and installed boot-repair and did the recommended repair. 
[paste.ubuntu.com/6107562]("paste.ubuntu.com/6107562")
I followed the boot repair instructions and disabled secure boot in my bios. Upon restarting I was greeted with the "No bootable device available!!!" message
I looked in my BIOS and I noticed that Boot Mode was set to Legacy. When I change that to UEFI and reboot, I'm presented with a blank screen that flashes ever five seconds or so.
If I set Secure Boot to enabled I also get "No bootable device available!!!"

Thank you in advance for your help.

---

### Post by oldfred on 2013-09-14
Boot-Repair is having all sorts of issues. Did you not turn fast boot off? That is the always on hibernation and creates all sorts of issues with any sort of dual booting, but does make Windows boot faster.

With secure boot on, only systems that are secure boot will be offered or be bootable. Ubuntu was not installed in secure boot mode.
If looks like because of the issues Boot-Repair ran the file rename. That is for those systems that have hard coded UEFI to only boot the Windows efi file. I might undo the rename and see if you can directly boot Windows. Then make sure fast boot is off. Both Windows & ubuntu should boot from UEFI menu in UEFI mode but with secure boot off. Some only boot with secure boot on.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

    This is what was renamed:
 Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

Users may have posted some info here also:
 [SOLVED] Dual-boot Ubuntu/Windows8 on Dell XPS 8500, need just a few advices with info on UEFI settings
[http://ubuntuforums.org/showthread.php?t=2151494](http://ubuntuforums.org/showthread.php?t=2151494)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

---

### Post by B34N on 2013-09-14
oldfred: thank you for the help

I did what you suggested with [boot-repair]("http://paste.ubuntu.com/6108165") but I didn't let it repair the Windows EFI files. As per the linked posting, I set my boot options to:
Secure Boot state: Disabled (Default was Enabled)
Secure Boot: Disabled (Default was Enabled)
Load Legacy OPROM: Disabled (Default was Enabled)
Boot Mode: UEFI (Default was Legacy)

I can boot only into Windows 8. I turned off fast boot. And still the same.

What do I now need to do to get Ubuntu and Windows 8 running? boot-repair gave me a message to make sure that my bios boots on sda2/EFI/ubuntu/grubx64.efi but I can't figure out how to check that.

Thank you!

BTW: boot-repair is a really cool tool! It's super helpful for people like me.

---

### Post by oldfred on 2013-09-14
You should have another choice in UEFI menu for ubuntu which will be the grub boot file. Since not secure boot version it will only work with secure boot off.

If not post a new link to BootInfo report.

---

### Post by B34N on 2013-09-15
I played around in the BIOs and in th eboot section there was an advanced section for Hard Drives. I changed it from "Windows Boot Manager" to disabled. I then ran boot-repair which showed "Buggy-Kernal Detected". Now I get a Grub menu. here is the BootInfo report. just to confirm that the changes I made are what made the difference.
[paste.ubuntu.com/6110622]("http://paste.ubuntu.com/6110622")

Thank you!

---

### Post by oldfred on 2013-09-15
if your system only boots Windows which a few UEFI have been modified to do, then you cannot undo the rename of the Windows efi file. I think Boot-Repair saw issues and then thought it was one of the buggy UEFIs.

This is what it has done.
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

