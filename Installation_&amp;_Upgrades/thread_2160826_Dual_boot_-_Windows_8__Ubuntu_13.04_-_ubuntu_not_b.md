---
title: "Dual boot - Windows 8 / Ubuntu 13.04 - ubuntu not booting"
date: 2013-07-08
forum: Installation &amp; Upgrades
---

### Post by fmsthree on 2013-07-08
I had to manually Power Down my PC because it locked up running Ubuntu 13.04. When I tried to reboot, I get the following

An error occured while mounting /boot/efi
Press S to skip mounting or M for manual recovery.

I have tried to use boot-repair and I am able to boot into Windows 8, but that is NOT my preference. Booting into Ubuntu hangs at a blank screen before any information is displayed.

My boot-info is available at [http://paste.ubuntu.com/5854068](http://paste.ubuntu.com/5854068)

Any help or suggestions would be greatly appreciated.

---

### Post by fantab on 2013-07-08
Have you disabled 'Fast Startup' in Windows8? If not, then [disable 'Fast Startup']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").

> 
The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting),

---

### Post by fmsthree on 2013-07-08
> **fantab said:**
> Have you disabled 'Fast Startup' in Windows8? If not, then [disable 'Fast Startup']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").

thanks fantab, I made that change in Windows 8 and reran boot-repair. My new boot-info is at [http://paste.ubuntu.com/5855887](http://paste.ubuntu.com/5855887).

I didn't assume that you were suggesting that was all that was needed, and my problems still persist unchanged.

---

### Post by oldfred on 2013-07-08
Your original error on mounting your efi partition may need chkdsk from a Windows repair console. Not sure but I do not think Windows 8 mounts efi partition, so you have to use command line in Windows repair console, mount the partition that is the efi partition and run chkdsk. Do you have a separate Windows 8 repair flash drive? If not you should.

       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)


 Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by fmsthree on 2013-07-09
Thanks for all of the great information oldfred. I've run chkdsk on the EFI partition - no problems found. I've rerun boot-repair (not sure if I should keep running that over and over, but I have no other clues and find very little information online.) My new boot-info is at [http://paste.ubuntu.com/5857050](http://paste.ubuntu.com/5857050).

Thanks to anyone with suggestions.

---

### Post by oldfred on 2013-07-09
You have run the Boot-Repair rename function which is for those systems that only boot the Windows file. That converts the Windows efi file to really be grub's shim with the signing key. But you have not yet installed the signed kernel from Ubuntu, so Ubuntu will only boot with secure boot off, if you computer allows that. Some do not. And with the rename you do not have the Windows efi file.

You have done part of this, the rename, but not the boot with secure boot on and use Boot-Repair to install the signed kernel from Ubuntu. You can also do the unrename to restore direct booting of the Windows efi file.

 To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
It does this:
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

From grub menu the entry is mis-named as recover. Some systems do not seem to report which is recovery and which is Windows.

This is the renamed version of your actual Windows boot stanza. In menu you only see  menuentry.


>  menuentry "Windows UEFI recovery bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root B4D9-B91C
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

 




---

### Post by fmsthree on 2013-07-09
Wow oldfred (by the way, I am an old Fred as well) I really appreciate all of the information and effort to help.

I'm not entirely sure of the steps, so I thought I'd move slowly and give you the results so far.

I performed a boot-repair with the only changes to default is that I checked Backup and rename EFI files and then clicked Apply. The boot-info for that repair is [http://paste.ubuntu.com/5859251](http://paste.ubuntu.com/5859251). I then rebooted with EUFI and received the following - 

Ubuntu has been blocked by current security policy.
Windows Boot Manager has been blocked by current security policy.
Windows Boot Manager has been blocked by current security policy.

I then enabled secure boot in the EUFI/BIOS and rebooted using ubuntu live CD and ran boot-repair again. I click the SecureBoot option and hit apply and I get the following error in Ubuntu Live - 

Please disable SecureBoot in the BIOS. Then try again. Do you want to continue?

I'll wait for further instructions because I don't want to make too many changes at once.

---

### Post by oldfred on 2013-07-09
Your system must be one that does not comply with UEFI specs and has been modified to only boot Windows with secure boot on. Microsoft requires vendors to let you turn off secure boot, but does not specify that Windows should still boot or not. Some do and others do not boot Windows with secure boot off.

To boot Ubuntu then you need all the secure boot configuration. It did not look like you have installed grub's shim which has the Microsoft signing key and the signed kernel files. You have to boot live installer in secure boot mode with secure boot on and check the secure boot box in Boot-Repair and it will download the secure boot grub & kernel files into your install. Without the secure boot files, Ubuntu will only boot with secure boot off, and Windows will only boot with secure boot on. So then entries in grub menu will not work as one or the other is not configured correctly. The only way to boot Windows would be to undo the rename function which your system seems to need as it will only boot the Windows efi file.

I thought I had seen some Lenovo's boot Windows with secure boot off, but have not paid close attention as there are many vendors and an awful lot of models. And even different models seem to be different.
Have you updated to the latest version of UEFI/BIOS from Lenovo?

---

### Post by fmsthree on 2013-07-09
OK, so on the last post I made the error poped-up "Please disable SecureBoot in the BIOS. Then try again. Do you want to continue?" I chose continue and it seemed to install the shim. After completing the boot-repair, I rebooted and received the message again - "Ubuntu has been blocked by current security policy." I then turned off SecureBoot in the UEFI/BIOS and I'm back to where I was in the beginning - ubuntu starts to boot and the says "An error ocurred while mounting /boot/efi  Press S to skip or M for manual recovery"

I am able to boot in to Windows 8 still. And my BIOS version is 8.04 (not the newest).

---

### Post by oldfred on 2013-07-09
Your last BootInfo report showed this:
       /boot/vmlinuz-3.8.0-26-generic
    but you need the version that has -signed at the end.

       Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 
One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.



 Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

---

### Post by fmsthree on 2013-07-09
I'm sorry to keep coming back with bad news, but I still get the same error - 

An error ocurred while mounting /boot/efi

My new boot-info is at [http://paste.ubuntu.com/5859826/](http://paste.ubuntu.com/5859826/)

---

### Post by oldfred on 2013-07-09
You now show.
 /boot/vmlinuz-3.8.0-26-generic.efi.signed
Which should boot Ubuntu with secure boot on.

Are you booting Windows efi file from UEFI (the one that it thinks is Windows but is really shim)?
These are the renamed files which now only boot from grub menu as it knows new name, but you want to boot the unrenamed verison (no bkp at beginning)  from the UEFI menu.

 Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi

It looks like the current default is 0002 which is not shown? Not sure which is correct?
>  BootOrder: [COLOR=#ff0000]0002[/COLOR],0003,0005,0004,0000,0000,2001
Boot0000* Lenovo Recovery System    HD(3,276800,1f4000,6981013b-f319-49ce-ae1a-9972741ff6a7)File(EFIMicrosoftBootLrsBootMgr.efi)RC
Boot0001* EFI DVD/CDROM (hp DVDWBD TS-LB23L)    ACPI(a0341d0,0)PCI(1f,2)03120a00020000000000CD-ROM(1,6168c,11c0)RC
Boot[COLOR=#ff0000]0003[/COLOR]* Windows Boot Manager    HD(2,1f4800,82000,3ca23f6a-0bc3-4de6-ab77-16a443567d55)File(EFIMicrosoft[COLOR=#ff0000]Bootbootmgfw.efi[/COLOR])WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot[COLOR=#ff0000]0005[/COLOR]* Windows Boot Manager    HD(3,276800,1f4000,6981013b-f319-49ce-ae1a-9972741ff6a7)File(EFIMicrosoft[COLOR=#ff0000]Bootbootmgfw.efi[/COLOR])RC
Boot0006* EFI Network 0 for IPv6 (B8-88-E3-92-DC-C5)     ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(b888e392dcc5,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0007* EFI Network 0 for IPv4 (B8-88-E3-92-DC-C5)     ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(b888e392dcc5,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot2001* EFI USB Device    RC



---

### Post by fmsthree on 2013-07-10
Hi oldfred - I just want to say how thankful I am to you for your help. I'm very impressed with the help you're providing.

If I understand correctly, what you are referring to is the Boot Order in my BIOS and here is what is in my EFI list

Ubuntu (ST500LT012-9WS142)
EFI DVD/CDROM (hp DVDWBD TS-LB23L)
Windows Boot Manager (ST500LT012-9WS142)
Windows Boot Manager (ST500LT012-9WS142)
Ubuntu (ST500LT012-9WS142)
EFI Network 0 for IPv6 (B8-88-E3-92-DC-C5)
EFI Network 0 for IPv4 (B8-88-E3-92-DC-C5)
Lenovo Recovery system (ST500LT012-9WS142)

I understand that the order may have changed since my last Boot-Info since I've been manipulating this list to boot either into Windows 8 or the Ubuntu Live CD. I have cycled through the partitions, booting from each one - the 2 Windows Boot Manager partitions give me a message "Windows Boot Manager failed" and then revert to the Grub Menu that I get with the Ubuntu partitions, but none will allow me to boot Ubuntu.

---

### Post by oldfred on 2013-07-10
Is this with secure boot on? Or with it off?
Ubuntu should work with secure boot on or off, but you may also have other issues after grub menu. Many need a boot parameter depending on video card/chip used.
But Windows should boot with secure boot on, if when you last shut it down you had fastboot (hibernation) turned off.

The list of boot entries was from your BootInfo report which also queries the efi variables.

---

### Post by fmsthree on 2013-07-10
This is with SecureBoot ON. Windows doesn't seem to care either way (if I remember correctly), I've always been able to boot into Windows I'd just rather not :)

---

### Post by oldfred on 2013-07-10
Please review this bug report and see if it applies. Also some work arounds or ways to boot.

       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)
Windows will not chain load from grub -
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,96800,32000,7c043777b8608641,87,f6)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi

---

### Post by fmsthree on 2013-07-10
Thank you - I will see if I can get a workaround working and report back.

---

