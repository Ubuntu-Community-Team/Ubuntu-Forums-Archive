---
title: "install 20.4 alongside win 10 failed with 'grub-install/dev/sda' failed"
date: 2020-10-19
forum: Installation &amp; Upgrades
---

### Post by cimh on 2020-10-19
Hi been struggling with this for several hours. I have win 10 on a legacy bios. I had installed ubuntu20.04 successfully and dual booting fine. But silly me then decided to install LXQT 20.04 over that. This resulted in an abort at the grub stage and the grub rescue prompt and therefore no access to windows 10 any more. I then tried to reinstall ubuntu 20.04 thinking if it worked before perhaps it will work again. but this resulted in the fatal error at the end of the restore as in my title.

I suspect this is all to do with Bios and uefi, but how do i overcome it. I wonder if because I have lost access to windows and have had to make the usb using the linux version of unetbootin this is trying to create a uefi boot on a legacy system? 

If it helps GParted shows:
sda1   ntfs   winre  19G
sda2   ntfs   win 8  144G
sda4   extended
sda5   fat32            513M
sda6   fat32           512M   boot,esp
sda7   ext4       446G
sda3   ntfs           868M msftres

Any advice much appreciated as i am stuck

The good news is that my windows partitions are still visible. So potentially everything is recoverable. I have also tried to repair the boot from the windows side using a repair disc and the command prompt but to no avail. I guess if there is not easy linux fix then it might be best to wipe the pc and do a clean reinstall windows 10 first.

Thank you
CIMH

---

### Post by ubfan1 on 2020-10-19
Yes, looks like an attempt at a UEFI install was made, but putting the EFI partition on a logical disk probably wont work.  Check your BIOs/UEFI settings for how your install USB boots, that's how the install will be done.  Boot legacy, then do a grub-install on sda and you should be all set. Or maybe just putting legacy preferred over UEFI will let your existing system boot.

---

### Post by CelticWarrior on 2020-10-19
Honestly, it's baffling.

Since 2012 Microsoft requires vendors to install Windows in UEFI mode (where applicable) and UEFI existed in PCs years before that, in Apple machines even older.
And here we are just months away from 2021 and users still insist in doing Legacy installations (Windows in this case). Legacy/CSM/"BIOS" mode is still an option in the firmware for OSes that don't support UEFI mode and only those, which doesn't make much sense anyway because the last "BIOS only" Windows is XP, unsupported since 2014. 

I would take the opportunity and reinstall both OSes in UEFI mode as it should be and much easier and safer for dual-booting. But if you don't want to reinstall Windows, and assuming it's in Legacy mode, then you must boot and install Ubuntu in Legacy as well.

---

### Post by ajgreeny on 2020-10-19
I assume you must have installed Windows 10 yourself as it would appear to be using msdos/BIOS partitioning scheme instead of the expected UEFI/GPT.

To let us see the full story go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by cimh on 2020-10-19
Ajgreeny - Brilliant and thank you - However, I read your bit too quickly and ran the repair as everything seemed to be going well AND my pc now boots to the installed Ubuntu. Thats a very impressive script! No grub screen came up so I do not have a means of accessing windows as yet - But this is great - Can you guide me as to how we pick up Win 10? Hopefully this report might help? [https://paste.ubuntu.com/p/898yxJV7BN/](https://paste.ubuntu.com/p/898yxJV7BN/)    I can see it shows win10 on sda2 and it looks like it has boot files?

CelticWarrior - Thank you too. I think I have learnt my lesson and will not risk doing this again for a while while the PC is in legacy bios mode. It came with win8 but it is fast and meets my needs. Sounds like a fresh install of windows in uefi mode might be wise at some point if I continue to run linux and win10. However I might be able to move to Linux fully soon having discovered darktable which seems to be a v good raw image editor and 90% of all my other stuff is cloud based.

---

### Post by CelticWarrior on 2020-10-19
You can't dual-boot with the Grub menu with the systems installed in different mode.
To boot Windows you need to change the boot mode in UEFI and then it won't boot Ubuntu.

---

### Post by oldfred on 2020-10-19
Even though you booted installer & added Boot-Repair in UEFI mode, it looks like Boot-Repair was smart enough to know Windows in BIOS/MBR mode needed a BIOS version of grub and un-installed the UEFI version of grub. It also moved boot flag back to sda1 for Windows. 

UEFI & BIOS are not really compatible.
Once you start booting in one mode, you cannot switch, so grub can only boot other installs in same mode.
Windows only installs in UEFI mode to gpt partitioned drives.
Windows only installs in BIOS mode to MBR partitioned drives.
Ubuntu lets you install in UEFI mode to MBR drives, but really should not.

Part of issue is Windows in BIOS mode needs boot flag on the primary NTFS partition with its boot files.
But UEFI needs the boot,esp flags on the ESP - efi system partition. And only one boot flag per device/drive.

Dual booting with BIOS on one drive worked reasonably well with Windows 7.
But with Windows 10, it keeps turning on fast start up with update & then grub cannot boot it.
With UEFI, you just go to UEFI and boot Windows, fix Windows & boot Ubuntu again. Sometimes you have to change boot order in UEFI as updates do change that also.

But with BIOS you have to use your Windows repair disk, install Windows boot loader to MBR, fix Windows and then reinstall grub to MBR to dual boot, either manually or with Boot-Repair (actually easier manually, once you know how). Windows updates regularly, so becomes a regular hassle.

Or you always need good backups, and both a Windows repair flash drive and an Ubuntu live installer.

---

### Post by cimh on 2020-10-20
Thank you Oldfred and CelticWarrior. 
I am wondering whats the best solution if I want to keep dual boot for now? 
1. Get back access to windows in bios and from their reinstall ubuntu in bios? - sounds like this is possible but not a great idea? and it seems ubuntu install defaults to efi? 
2. Reinstall windows in efi mode - is this posible while keeping ubuntu as is?
3. Wipe the pc and do a clean install of both?

My windows documents / pictures are backed up on a NAS so I dont mind a clean install if thats best.  This PC hasn't been reset for at least 10yrs.

Thanks again for your support

Of interest the PC has 2 options for  the Bios Boot - UEFI & BIOS and UEFI
but which ever one I set it always boots into ubuntu but on both times the bios screen flashes up twice during the boot which is not normal. So presumably it tries to boot in bios fails and tries again in uefi?

---

### Post by CelticWarrior on 2020-10-20
#2 isn't possible, oldfred already exlained the requirements - GPT for UEFI -.
I would do #3 after converting the drive to GPT. That can be done with GParted in a Ubuntu live session. That also will delete everything in the drive.
Then select UEFI only to assure everything else from then on boots and installs in UEFI mode.

#1 is doable. It requires reinstalling Grub for BIOS mode.

---

### Post by cimh on 2020-10-20
CelticWarrior

Thank you I'll go for #3 and do a clean install of ubuntu on a fresh formatted drive. 

Just a few final checks - before casting off:-

1. Its ok to install ubuntu 1st then windows later?  
2. Do I switch the bios to uefi prior to doing the ubuntu install?
3. Will the ubuntu install do all the work for me automatically or do I have to do the conversion from MBR to GPT separately?

---

### Post by oldfred on 2020-10-20
How you boot install media UEFI or BIOS is then how it installs for both Windows & Ubuntu.
Windows only installs in UEFI mode to gpt partitioned drive. If it sees MBR it will not install. And it needs unallocated space.
Ubuntu does let you install in UEFI mode to MBR drive, and really should not. It only creates gpt if drive is blank.

You can convert in place with gdisk, but Windows has major differences in partition requirements.
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by cimh on 2020-10-22
Oldfred  and others thanks again for all your help.

I have done a clean install windows 10 (knowing that it would force my hdd into GPT and UEFI. I let windows format 1/2 the HDD. leaving the other 1/2 for Ubuntu.
I made a usb of the ubuntu iso using rufus which lets the usb to be formatted to gpt and efi.
When installing Ubuntu it identified windows and I clicked 'other' to format the remaining part of the HDD as an ext4 partion mounted as \ for ubuntu - No problems

It all works except that the PC automatically boots to windows, rather than coming up with the ubuntu grub which would also offer the choice of OSs to launch. 

So looking at the efi section I can see
efi\ms\Boot\bootmgfw.efi
efi\ubuntu\shimx64.efi
efi\ubuntu\grub64.efi

Some forums suggest that the following windows command will point the boot from the windows boot manager to ubuntu

bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

But some other comments suggest that this might not be a permanent fix - so I think I'll play safe for now - the PC can automatically boot to windows - which will be great for my wife and i I want linux I can press F11 during boot and then select ubuntu.

So I guess my issue is solved thanks to everyone's help

---

### Post by CelticWarrior on 2020-10-22
Have you already checked the UEFI settings > Boot?

You should because probably all you need to do is to change from "WIndows bootloader manager" to "Ubuntu". This is because the Ubuntu installation not always change this setting but it can be done manually.

---

### Post by cimh on 2020-10-22
CelticWarrior THANK YOU again. In my MSI legacy startup it was obvious how to change boot priorities. But in UEFI all I could see was a list of 'fixed boot priorities' which I couldn't change and in which ubuntu did not appear anyway - so I thought that was that. However after your comment I can see lower down the page there is a link to "UEFI HDD BBS priorities" This shows a list of the 3 efi boots on the hard drive and this section lets me direct the boot to ubuntu rather than windows. So it all makes sense and the dual boot now works perfectly.

Many thanks - I have learnt something - I appreciate your patience!

cimh

---

