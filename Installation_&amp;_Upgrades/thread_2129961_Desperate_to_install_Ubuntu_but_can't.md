---
title: "Desperate to install Ubuntu but can't"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by jimfl on 2013-03-27
[COLOR=#000000][FONT=times new roman]I love Ubuntu. Ran it for three years on my Dell that died this morning. Replaced it with a Lenovo IdeaCentre K410 Pentium 64-bit. Learned to hate Windows 8 in a matter of minutes. Downloaded the 781 mb i386 installation file iso. Burned it to DVD. Lenovo wouldn't boot from the DVD. Clicked on Wubi and clicked on Help Me to Boot from CD. Wubi installed "new boot menu entry." Rebooted. Screen gave me a choice of clicking on Windows or Ubuntu. Clicked on Ubuntu. Got error message from Windows Boot Manager saying Windows failed to start.  Retried from beginning downloading the amd64.iso file. Followed same procedure. Got identical results.
 
HELP!!!
[/FONT][/COLOR]

---

### Post by oldfred on 2013-03-28
Wubi does not work with gpt partitioned drives. And UEFI and Windows 8 pre-installed uses UEFI with gpt partitioning.

       Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

Repair Windows, make backups of both efi partition and Windows. Use Windows disk tools to shrink the Windows partition and reboot a couple of times so it can run chkdsk and make its repairs to its new size.

      
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

      
 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

Some other Lenovo that seem to have worked.

 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)

---

### Post by jimfl on 2013-03-28
Good graceful heavens. Can it possibly be this hard? I don't want to keep Windows.  It used to be pretty easy to replace it with Ubuntu--just download the file, burn it to CD, boot it and follow the instructions. Although I_ greatly _appreciate your response, I really doubt I'll be able to follow the instructions. They look to be well beyond my level. For example: backing up efi partition (need to do if I want to wipe Windows?)?; booting in UEFI mode?; etc.

---

### Post by oldfred on 2013-03-28
If you are totally wiping Windows and are sure you will not go back, then you can just over install. But we often get users who have one program or game that does not work in Ubuntu and want Windows back later. Many also should backup Windows as later if they want to sell computer, the buyer may require Windows.

If it is a new system, you really should run the 64 bit version.

System has secure boot. Microsoft says vendors should allow users to turn secure boot off, but some only boot Windows efi boot file with the Microsoft key.

You also have CSM or the old BIOS legacy boot mode. Which may be easier to deal with if you do not ever want Windows. Windows will only boot on gpt partitioned drive with UEFI.

If in BIOS mode with gpt partitioning Ubuntu will install but needs a tiny 1MB unformatted bios_grub partition.I have an older system with only BIOS and now use gpt partitioned drives.

So UEFI/BIOS settings become very important and with the new UEFI they may be even more complex. But turn off fast boot, secure boot, and if you want CSM/BIOS turn that on.

From UEFI/BIOS how you boot installer is how it installs. You should see two boot choices UEFI and something else that is the CSM/legacy/BIOS mode.

---

### Post by jimfl on 2013-03-28
Yes, I'm sure about wiping Windows. Haven't used it for 3 years and have found open source programs for everything I need.

What I really need is a List of Steps for Dummies, I guess.

If I understand you, I need to turn off secure boot and fast boot and select to boot with Legacy mode. I think I've seen where to do that. Then if I boot with the 64-bit iso DVD, is that what I need to do?

---

### Post by oldfred on 2013-03-28
I have seen several users do just that and it has worked for them. I now prefer flash drives over DVDs. Reuseable and a bit quicker.
Have you tested in Live mode to make sure everything works?

But a few Windows 8 computers seem to have UEFI that only works with Windows, which should not be the case. Microsoft requires vendors to allow users to turn secure boot off, but does not specify anything on what may or may not work with secure boot off.
Some seem to have a one key recovery mode. Where it is easy just to reset to as installed.

---

### Post by jimfl on 2013-03-28
I turned off secure boot and fast boot and selected to boot with Legacy mode.  (Had the 64-bit iso in the DVD drive.) Then I got the choice to use Windows or Ubuntu. Chose Ubuntu but got the same error message from Windows Boot Manager saying Windows failed to start.[COLOR=#000000][FONT=times new roman].[/FONT][/COLOR]

---

### Post by oldefoxx on 2013-03-28
You guys are over my head, and my PCs aren't that new so I haven't run into this myself.  What did work for me one time was to download the boot version of gparted and just repartition and format my hard drive for Ext3, then go through the install process from a CD for Ubuntu.

In my BIOS settings, I can change the boot devices and order of attempts.  Might that help?  Sometimes going at a problem a different way can make the difference.  Like mounting an internal drive as an external to another PC and having your way with it there first.

---

### Post by honeybear on 2013-03-28
hi

have you tried Debian, it is very probably better, more stable, and working? You really wont notice that it is not ubuntu.

regards

---

### Post by oldfred on 2013-03-28
I do not think Debian has UEFI support. If just erasing drive and installing totally new, you can use Ubuntu or just about anything else in CSM/Legacy/BIOS mode. 

This whole UEFI/gpt partitioning is all new. So all that old info we accumulated over the last 30 years on BIOS booting with MBR(msdos) partitioning is now obsolete.

Have you installed? Is install in BIOS mode. Then you have to boot in CSM mode.
May be best to post link to BootInfo. Boot Repair also can convert a BIOS install to UEFI, as some seem to work better that way, But just post link for now.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by jimfl on 2013-03-30
This is somewhere way beyond frustrating. I found at lenovo.com/support how to boot from the DVD drive. Booted from my 64-bit Ubuntu iso, and it worked. Went all through the complete installation process (dual boot). Got the message that the install was successful and that I should reboot. But when I did, I got the same old message from Windows Boot Manager saying Windows failed to start. 

I created a Boot Repair disk but the Lenovo won't boot from it so I can't append a BootInfo report.
My BIOS is currently set up this way:
CSM   enabled
Bootmode   Auto
Boot priority    Legacy first
Quick Boot    Disabled
Rapid Boot   Disabled

By the way, here are the instructions from Lenovo on booting from CD/DVD in case they might help somebody:

To boot to Legacy devices, it is necessary to disable Microsoft Windows 8 default settings in the Setup Utility:

[LIST=1]
[*]Restart the  PC and press F1 to enter Setup.
[*]For ThinkPad:  Navigate to the RESTART menu. 
 For  ThinkCentre and ThinkStation:  Navigate to the EXIT menu
[*]Select OS Optimized Defaults and change  the value to Disabled.
[*]Select Yes to continue to disable the  OS Optimized Defaults.
[*]Press F9 to load Setup Defaults.
[*]Select Yes to confirm the loading  default configuration.
[*]Press F10 to save and exit Setup.
[*]If necessary,  press F12 to access the boot menu and select your boot device.
[/LIST]
 
[TABLE="width: 100%"]
[TR]
[TH="class: yiv1178729378v14-header-1"]Additional Information
[/TH]
[/TR]
[/TABLE]
Microsoft requires Lenovo to configure all Microsoft Windows 8 PCs with the following UEFI firmware (BIOS) settings:

[LIST]
[*]UEFI only
[*]Secure Boot
[/LIST]

With  these settings, it is not possible to boot a Legacy operating system  such as DOS or Microsoft Windows XP.  Also, it is not possible to boot  an operating system that is not enabled for Secure Boot, such as  Microsoft Windows 7 and certain Linux distributions. 

For these  reasons, it is not possible to boot many existing diagnostic or  backup/restore tools on a Microsoft Windows 8 PC with default UEFI  firmware (BIOS) settings.

---

### Post by oldfred on 2013-03-30
If you were in CSM or BIOS mode, you installed Ubuntu in BIOS mode which is not UEFI nor secure boot mode. But Boot-Repair will convert a BIOS install to UEFI with secure boot files. But you have to boot in UEFI mode. It should boot with secure boot as Ubuntu has that. It actually uses the Microsoft secure boot key.

---

### Post by jimfl on 2013-03-30
Thank goodness! I've got Ubuntu back at last. Disabling CSM did the trick (didn't have to use Boot Repair). I no longer can boot into Windows, though.  Not a big problem since I don't like it, don't trust it, and don't use it.  Thanks to oldfred for all your patient help.  One last question:  do you think if I run Boot Repair I would regain the ability to boot Windows if I ever wanted to use it?

---

### Post by oldfred on 2013-03-30
Many have used Boot-Repair to fix UEFI issues. Are you actually booting with UEFI now or in BIOS/Legacy/CSM mode? Either way I would back up efi partition and Windows.

But the options and settings get complex as some dual boot without much issue as Ubuntu has the Microsoft key. Some have modifed UEFI code to only boot Windows efi file. For those systems you have to use Boot-Repair to rename files so UEFI thinks it is booting Windows when it is really booting Ubuntu.

Many have issues just finding the correct ubuntu entry in the UEFI menu, but it is there.

If you installed in BIOS/CSM/Legacy mode, Boot-Repair converts to UEFI.
         How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

   
Only if you have a system with modified UEFI that only boots Windows efi file, then you can use the rename function to make it work.
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi

---

### Post by jimfl on 2013-04-03
Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

---

### Post by oldfred on 2013-04-03
I would think that if you can directly boot Windows, the Windows efi boot entry that Boot-Repair added in grub should work.

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by jimfl on 2013-05-01
I'm BAACCKKK.  Everything was working fine (I could boot into Windows or  Ubuntu 12.10), but then I upgraded to 13.04 and now I can only boot  into Windows. My UEFI settings are:
Secure Boot     disabled
CSM     enabled  (have tried disabled, too)
Boot Mode    Auto
Boot Priority     UEFI  (have tried Legacy first, too)
Quick Boot     disabled
Rapid Boot     disabled

When I turn on the computer, I get this message:   Syslinux 3.63 Debian 2008-07-15 EBIOS Copyright 1994-2008 H. Peter Anvin
Boot:
(If I hit enter at this point, I get the message:  "Could not find kernel image: linux 

When I repeatedly press F12 on start-up and then choose to boot into Ubuntu, I again get this message and command prompt:  Syslinux 3.63 Debian 2008-07-15 EBIOS Copyright 1994-2008 H. Peter Anvin
Boot:

I downloaded boot-repair-disk and copied it to a USB drive and then try to boot from the USB but it won't start boot-repair.

Please help.

---

### Post by oldfred on 2013-05-01
How did you upgrade?

The syslinux message is from a USB flash drive, or did you install ISO to hard drive? Usually the USB installer totally erases the drive it installs into.

But you should be able to from UEFI withsecure boot off boot live install in flash drive or Boot-Repair if you downloaded its 12.10 secure remix. The older version may not work.
You may want CSM or BIOS mode off, so it does boot in UEFI mode.

---

### Post by jimfl on 2013-05-07
Semi-success. By disabling CSM I can now boot into Ubuntu 13.04.  However, to do so I have to repeatedly push F12 during startup to access  the Boot Sequence screen. Otherwise I just get the same old message saying that Windows failed to open and listing the problem as /ubuntu/winboot/wubildr.mbr . 

I've copied boot-repair-disk to both a CD and a thumb drive, but neither will load at startup even though I select to either boot from DVD drive or USB drive.

Any suggestions?

---

### Post by oldfred on 2013-05-07
If you can boot into Ubuntu you can download and run Boot-Repair from there. Post link to new BootInfo report.

You really have to have a bootable flash drive to make repairs. Are you booting with the full 13.04 ISO installed to a flash drive with unetbootin or other flash drive installer? If in Ubuntu the startup disk creator works.

       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

      
 [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You do need to boot flash drive in UEFI mode not BIOS/CSM/Legacy mode.

---

### Post by jimfl on 2013-05-07
Okay, I've created a bootable USB drive with the full Ubuntu 64-bit iso on it, and I can now boot from that. However, I still can't figure out how to run boot-repair. I copied the boot-repair iso to the USB drive but I can't figure how how to install it. Is there a command to use in Terminal?

---

### Post by oldfred on 2013-05-07
With a live installer, you just boot and then install from the Internet the Boot-Repair. Or download the Boot-Repair ISO versions that include Boot-Repair in the ISO.

You can turn persistence on and then some things can be saved with a live installer.
       
Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

             [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
    
Boot-Repair now has a newer lighter weight verison, but it is just a repairCD not an installer.
       LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by jimfl on 2013-05-08
Well, I found out how to install boot-repair on this page:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

And I can now boot into Ubuntu with the option of starting Windows without having to press F12.

Thanks VERY much for your help, OldFred.

I have to say, though, that it was a major hassle to resolve this issue which was caused by my upgrade to Ubuntu 13.04. It will be a long time before I upgrade again, and that's for sure!

I wonder how many people, instead of spending all the time I did, just give up on Ubuntu and stick with Windows. I hope this issue will be addressed and resolved as soon as possible because it used to be so simple and straightforward to do an Ubuntu upgrade.

---

### Post by oldfred on 2013-05-08
Glad you got it working. :)

One disadvantage of 13.04 is a short support time. So you will be upgrading in 9 months. 

Those with the last Windows 7 that did have UEFI, often just installed without issue. A few bugs like os-prober that is still there, but the real issue is the secure boot. I think secure is Windows business model not anything to do with computer security.

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

