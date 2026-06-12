---
title: "Want to change Ubuntu from UEFI to Legacy so as to be able to dual boot with Windows"
date: 2020-04-15
forum: Installation &amp; Upgrades
---

### Post by zayn-darkmore on 2020-04-15
I'm extremely new to Ubuntu and have almost no knowledge using it.
I have an HP Compaq 8200 Elite Microtower that came with Windows 7 32 bit pre-installed in Legacy mode. Later, I updated this to Windows 10 32 bit in Legacy Mode. Although my CPU is fully 64 bit capable, I didn't think of installing a 64 bit Windows.
Now I tried to install Ubuntu 18.04 64 bit on this system. I did this via a USB Flash Drive.
The USB Flash Drive always boots in UEFI, so during the install Ubuntu didn't detect my Windows Installation. I chose 'Something Else' created a root and a home partition, and when prompted, a efi system partition.
The installation completed and I found out that as _Ubuntu was in UEFI boot, the grub menu did not have any option to boot into Windows 10 Legacy_. Since the install I have not been able to boot into WIndows 10. 
I thought that if I could convert Ubuntu from UEFI to a Legacy mode, this problem would be fixed.
The official Ubuntu website has a guide for GPT disks but as I checked right now my disk is an MBR. Other solutions on the internet similarly had differences from my situation
What should I do?

---

### Post by yancek on 2020-04-15
Have you read the Ubuntu documentation at the page at the link below?  I'd suggest you review it as it should answer some of your questions including how to convert to Legacy mode..  When you installed Ubuntu, did you have Legacy/CSM enabled in the BIOS firmware?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by TheFu on 2020-04-15
I don't dual boot.

Windows requires GPT for UEFI booting.  Linux does not, but some hardware/BIOS limits could.  I've not seen that on any of my hardware, but some people have.

All installed OSes that are directly booted from the hardware need to be in the same mode - all UEFI or all Legacy BIOS.  Which you go with is up to you and each has pros and cons.  The Linux Foundation Workstation Security Checklist recommends using UEFI with Secure Boot.

As yancek suggests, read that UEFI link carefully. Ask questions if it isn't clear.

Rather than dual booting, I use virtualization or LXD containers.  I don't know anything about that HP device to recommend any specific method over the other.

If it were me, I'd do my normal backup, then reinstall the base OS as is the procedure for my backup method.  My backups aren't tied to hardware, so changing the underlying install type, disk layout, and pretty much any hardware doesn't really impact the restore process.

---

### Post by zayn-darkmore on 2020-04-15
yancek
I just read it. But like I mentioned, the guide for converting a UEFI to Legacy requires you to ensure Linux is installed on GPT. Whereas, it is installed on an MBR for me. I do not know if this will create problems, hence I did not follow it.

No, Legacy was not enabled. My BIOS settings are a little messed up, so there's no priority order. To add to the confusion, USB Flash drives always boot from UEFI (So I found no way to install Ubuntu with Legacy BIOS)
You can however, disable UEFI boots entirely, in which case it would always ignore the flash drive and boot to Windows.
Simply put, the Flash drive booted in UEFI, and the installation was done as a UEFI boot. Now I have no way to boot into Windows

TheFu
My Windows 10 has a MBR disc and boots in BIOS (Legacy). As I found out, Linux could boot in either, but even when I manage to boot it in Legacy mode, the grub menu doesn't appear. It always boots to Ubuntu no matter what.
If there is an alternative method that I can use to boot into Windows I don't mind using that either.

At this point I do not know how to proceed with anything, as most of the guides trying to fix this by reinstalling Linux require me to boot into Windows, which I cannot

---

### Post by CelticWarrior on 2020-04-15
A few comments/corrections:

> the guide for converting a UEFI to Legacy requires you to ensure Linux  is installed on GPT. Whereas, it is installed on an MBR for me. I do not  know if this will create problems, hence I did not follow it.


No, the guide *assumes* Ubuntu installed in a GPT drive because that is the typical situation for any OS in UEFI mode. Again, it's important to note that Windows has strict requirements - MBR for BIOS/Legacy/CSM and GPT for UEFI - but Ubuntu has not. If yours is in a MBR drive, no problem. Or, yes, problem. I would reinstall both OSes in GPT/UEFI.

> To add to the confusion, USB Flash drives always boot from UEFI (So I found no way to install Ubuntu with Legacy BIOS)
You can however, disable UEFI boots entirely, in which case it would always ignore the flash drive and boot to Windows.

IF you had selected Legacy first then any properly made USB installer would boot in Legacy/CSM mode. The problem is typically USBs made with Rufus that, using the standard method instead of DD, only boot in one mode or another, depending on the settings. Any USB burned with any other tool that relies on DD does a bit-by-bit copy of the Ubuntu's hybrid ISO and that boots either way.

I can0't stress this enough: Install in UEFI mode whenever possible. Both Ubuntu and Windows will tank you for that. Furthermore, your computer is 64-bit so, preferably install 64-bit OSes only, Windows or Ubuntu. So, I would reinstall both after nuking everything in the drive while converting to GPT, in UEFI mode.

---

### Post by dragonfly41 on 2020-04-15
My dual boot configuration has UEFI throughout for Windows 10 and Ubuntu 18.04.
Moreover I use rEFInd as my bootloader,
I thought that rEFInd demands UEFI and does not work with mixed mbr and gpt.
But it seems from reading [this thread]("https://superuser.com/questions/1133040/unable-to-boot-into-windows-10-with-refind-solved") that this option is possible.
I offer no guarantee that it will work but usually rEFInd can dig you out of a hole.
You can install it through your Ubuntu OS then target the partition to install.  You can install in both Windows and Ubuntu.

But I add a note. UEFI + 64bit throughout is *much preferred*. Treat this exercise as a learning experience.

---

### Post by CelticWarrior on 2020-04-15
> My Windows 10 has a MBR disc and boots in BIOS (Legacy). As I found out,  Linux could boot in either, but even when I manage to boot it in Legacy  mode, the grub menu doesn't appear. It always boots to Ubuntu no matter  what.

Please boot Ubuntu and then run in terminal:
```
sudo upgrade-grub
```
Is Windows detected or not? Keep us posted.

With some luck it'll be detected, added to the Grub menu and boot normally. But very likely will not due to having the default Fast Startup feature enabled. This wouldn't be a problem in the original Windows 7. It is a problem in any Windows 8 or newer.

---

### Post by oldfred on 2020-04-15
There are two PC versions of grub, grub-pc for BIOS boot and grub-efi-amd64 (plus others for totally different systems).

Reinstalling grub will convert system from UEFI to BIOS or vice-versa. Doing that also changes the few settings that are different like fstab mount of ESP. If you boot Ubuntu live installer in BIOS mode and add Boot-Repair, it can in advanced options do a total reinstall of grub. It also can be done from inside Ubuntu, but system may not be bootable if it does not fully complete.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If you want BIOS on gpt with UBuntu, you have to have a bios_grub partition, but that is not required with MBR.

Windows 10 and BIOS dual boot on same drive with Ubuntu is not easily maintained.
Grub only boots working Windows, but Windows updates turn fast start back on, and then grub will not boot it. Or if Windows needs chkdsk grub will not boot it. And only ways to fix Windows is maybe temporarily restore Windows boot loader, fix Windows & restore grub2 boot loader to MBR. Or use Windows repair flash drive.

Best to have both systems in UEFI mode, but that would be a total reinstall of Windows & Ubuntu as it requires gpt and lots more partitions.

But if keeping BIOS/MBR, make sure you always have both a Windows repair flash drive and the Ubuntu live installer, so you can make repairs when it breaks. Good idea to have these even if UEFI installs. And good backups.

Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)

---

### Post by zayn-darkmore on 2020-04-15
> **CelticWarrior said:**
> Please boot Ubuntu and then run in terminal:
```
sudo upgrade-grub
```
Is Windows detected or not? Keep us posted.


I ran into an error.
sudo: upgrade-grub: command not found

---

### Post by ubfan1 on 2020-04-15
Oops that should have been sudo update-grub  But OldFred's post about installing the grub-pc package, and install that version of grub should fix things (with his warnings about future Windows interference).  I am running on such an MBR Win10/Ubuntu 18.04/16.04  triple boot and don't see any Windows update problems (but my UEFI 64 bit system si pre secure boot).

---

### Post by zayn-darkmore on 2020-04-15
Okay so the general opinion of everybody seems to be that I should clear up everything and start afresh. 
The main reason why I hesitate to do so is because due to the lockdown and stuff, I have around 8 hours of online classes everyday which means my computer is quite busy. I'd have only two days to get it right, and seeing me mess up, I feel way too scared to do that right now. I will do this as soon as the lockdowns lift and the computer usage goes down.
Currently I shall try the refind approach as suggested by dragonfly41.
It is alright to tag this thread [solved] after I actually try out the solutions, right?

Also a few questions about nuking everything and starting afresh- 
1) Since Ubuntu is correctly installed (UEFI, 64-bit) must I actually reinstall it?
2) If i needn't reinstall, could I wipe the Windows partitions while keeping Ubuntu installed? (Essentially try to dual boot again as if the original OS was Ubuntu)

> **ubfan1 said:**
> Oops that should have been sudo update-grub  But OldFred's post about installing the grub-pc package, and install that version of grub should fix things (with his warnings about future Windows interference)

Could somebody guide me on how I should go about this?

> **CelticWarrior said:**
> Please boot Ubuntu and then run in terminal:
```
sudo upgrade-grub
```
Is Windows detected or not? Keep us posted.

With some luck it'll be detected, added to the Grub menu and boot normally. But very likely will not due to having the default Fast Startup feature enabled. This wouldn't be a problem in the original Windows 7. It is a problem in any Windows 8 or newer.

I did _sudo update-grub _as corrected by ubfan1. Then rebooted. The grub menu doesn't appear and the system boots directly to Ubuntu.

---

### Post by TheFu on 2020-04-15
> **zayn-darkmore said:**
> Okay so the general opinion of everybody seems to be that I should clear up everything and start afresh. 
The main reason why I hesitate to do so is because due to the lockdown and stuff, I have around 8 hours of online classes everyday which means my computer is quite busy. I'd have only two days to get it right, and seeing me mess up, I feel way too scared to do that right now. I will do this as soon as the lockdowns lift and the computer usage goes down. 

In that situation, I'd definitely switch from dual boot to using a virtual machine for one of the OSes.  VMs are very low risk and don't modify the booting for any OS the isn't running inside a VM as a guest.  Any Core2 Duo or faster system can easily be a VM host machine, provided it has more than 2GB of RAM.

Do a little reading about virtual machines, watch a few youtube videos and see if it might be useful for you.  
For Windows as the host, **virtualbox** is a commonly used VM program to run other OSes inside.  
With Linux as the host, there are lots and lots of choices, including virtualbox.  I've never gotten virtualbox working on Linux myself, but lots of people use it.

Using VMs rather than dual booting is much, much, safer.

BTW, reinstalling Ubuntu is only 15 minutes. What makes you afraid to do that?  If you keep your data and settings separate, which is what a HOME directory is all about on any Unix-like system, then there isn't much to lose provided that is backed up before starting over.

---

### Post by dragonfly41 on 2020-04-15
If you can refurbish an old disk drive lying around somewhere you have the option of creating an* external Ubuntu* if you can place the drive in a USB container.
Most of my activity now is using external Ubuntu and there is no significant loss of performance. This post is being written on external Ubuntu.

With the security of an external Ubuntu you can consider your options on Windows.
I have created an ntfs partition on my external Ubuntu (SSD ext4) into which I can backup Windows files.

---

### Post by oldfred on 2020-04-15
Windows only installs in UEFI mode to gpt partitioned drives.
And if drive is not gpt, that will erase it, and then your Ubuntu.
If gpt, I am not sure what Windows does as it does not normally see Linux partitions, so good backups are vital.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Lots of info on UEFI install of Ubuntu in link below in my signature.

---

### Post by zayn-darkmore on 2020-04-15
> **TheFu said:**
> In that situation, I'd definitely switch from dual boot to using a virtual machine for one of the OSes.  VMs are very low risk and don't modify the booting for any OS the isn't running inside a VM as a guest.  Any Core2 Duo or faster system can easily be a VM host machine, provided it has more than 2GB of RAM.

Do a little reading about virtual machines, watch a few youtube videos and see if it might be useful for you.  
For Windows as the host, **virtualbox** is a commonly used VM program to run other OSes inside.  
With Linux as the host, there are lots and lots of choices, including virtualbox.  I've never gotten virtualbox working on Linux myself, but lots of people use it.

Using VMs rather than dual booting is much, much, safer.

BTW, reinstalling Ubuntu is only 15 minutes. What makes you afraid to do that?  If you keep your data and settings separate, which is what a HOME directory is all about on any Unix-like system, then there isn't much to lose provided that is backed up before starting over.

I have tried Virtual Machines long back while I only had Windows. I could never get it to work unfortunately:(. Which is why I opted for a dual boot recently.
To reinstall Ubuntu (with Legacy BIOS, which should solve the problem) how should I create the installation media such that it boots in Legacy Mode?

> **dragonfly41 said:**
> If you can refurbish an old disk drive lying around somewhere you have the option of creating an* external Ubuntu* if you can place the drive in a USB container.

This is not possible as I cannot obtain an old disk drive right now. But I would consider this for future attempts.

> **oldfred said:**
> Windows only installs in UEFI mode to gpt partitioned drives.
And if drive is not gpt, that will erase it, and then your Ubuntu.
If gpt, I am not sure what Windows does as it does not normally see Linux partitions, so good backups are vital.


I do not understand. So do you mean to say that if I create a Windows Installation Media and try to install it in UEFI, the install won't happen as my disks are all MBR?
How should I proceed if that is the case?

---

### Post by oldfred on 2020-04-15
Not sure if it just does not install if MBR with NTFS partitions, or just erases entire drive in conversion from MBR to gpt.
If you have good backups, it will not matter.

Both Windows & Ubuntu install in the boot mode you use for installer, UEFI or BIOS.
So you need to always boot in UEFI mode, if you want to install or repair in UEFI mode.

Both Windows and Ubuntu live installer ISO are configured for either UEFI or BIOS install. But some tools to create installer may only offer one or the other. And UEFI should offer two boot options for flash drive, one clearly UEFI:flash and other just "flash" where flash is name or label of flash drive. Mine shows as [noparse] UEFI:PMAP[/noparse]  or PMAP. Some UEFIs show UEFI boot entries totally separate, other just show all boot options together.

---

### Post by ubfan1 on 2020-04-15
The standard Ubuntu ISO is set up to boot both ways, so straight copy to USB like you'd get with dd will allow a legacy boot if your machine is/can be set up for a legacy usb boot. Getting rid of the UEFI boot may be as simple as getting rid of the EFI directory with the UEFI bootoaders, but the ISO's 9660 filessytem is read-only, so likewise the copied USB. Maybe a tool like mkusb will create a USB with a writeable root which you can alter, not sure.  

Windows will install/boot in UEFI mode only on gpt partitioned disks.  In theory, maybe you could convert the MBR partitioning to GPT, but the risk of losing the Ubuntu partitions prevented me from trying that.  If you're well backed up however...\\

You've got the Ubuntu install (done in UEFI mode), so really all you need is grub installed in legacy mode (package grub-pc).  I think that was what OldFred suggested.  The actual difference in the two installs is trivial, I've done the reverse, installing Ubuntu in legacy to another disk, then booting/running it in UEFI mode by simply dumping in the EFI/ubuntu and EFI/Boot bootloaders (copied off another system) into the EFI partition).  That runs.  You can add a mount point, /boot/efi for the EFI partition and the matching /etc/fstab mount line, but all that does is to allow updates to the bootloaders, and if you never get around to installing the grub-efi-amd64 package, that will never happen.  My biggest surprise is that the "legacy" grub.cfg still boots just fine when booting the device in UEFI mode, and updates as expected. I see no reason a legacy grub would not boot your UEFI Ubuntu install.  Maybe install the legacy grub to a USB stick and see if all the OSe are picked up.

Definitely some risk involved, so have backups you know you can restore.  And if the shutdown makes getting hands on help not possible, then delay if you can.  Look again at your BIOS settings some odd thing like Windows/Other may actually control boot capability.

---

### Post by zayn-darkmore on 2020-04-16
> **oldfred said:**
>  And UEFI should offer two boot options for flash drive, one clearly UEFI:flash and other just "flash" where flash is name or label of flash drive. Mine shows as [noparse] UEFI:PMAP[/noparse]  or PMAP. Some UEFIs show UEFI boot entries totally separate, other just show all boot options together.

This does not happen. Even when I go into the Boot Menu, the flash drive only shows up as a UEFI boot. The Boot Menu has the UEFI and Legacy Boot devices separated.

> **ubfan1 said:**
>  so really all you need is grub installed in legacy mode (package grub-pc).  I think that was what OldFred suggested.

This is exactly what I do not know how to do. Could someone tell me how to do this, or point me to a guide?

---

### Post by oldfred on 2020-04-16
I have seen Rufus screens that show option. MBR & CSM(UEFI) or gpt & UEFI. 
So I think it only makes ISO boot one way or other. Most tools create it so it can boot both ways.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by CelticWarrior on 2020-04-16
> **oldfred said:**
> Not sure if it just does not install if MBR with NTFS partitions, or just erases entire drive in conversion from MBR to gpt.

The Windows installer does everything regarding the partitioning **except** converting from MBR to GPT or vice-versa. I've confirmed this is several machines. Users must prepare the drives before booting the Windows installer. The Ubuntu live session, thanks to GParted and other CLI tools, can do everything. The Windows installer works fine with blank drives but if already MBR with or without partitions and booted in UEFI mode it won't proceed with the installation.

---

### Post by ubfan1 on 2020-04-16
Run Ubuntu, and in a terminal:
sudo apt-get install grub-pc
should install the legacy grub from a UEFI booted Ubuntu.
Then you should be able to select legacy instead of UEFI and boot, and legacy Windows should be offered too.

---

### Post by zayn-darkmore on 2020-04-17
> **oldfred said:**
> I have seen Rufus screens that show option. MBR & CSM(UEFI) or gpt & UEFI. 
So I think it only makes ISO boot one way or other. Most tools create it so it can boot both ways.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

This is probably what made mine force boot in UEFI, because I made my Ubuntu disc on Windows using Rufus. I will take care of this the next time.

> **ubfan1 said:**
> Run Ubuntu, and in a terminal:
sudo apt-get install grub-pc
should install the legacy grub from a UEFI booted Ubuntu.
Then you should be able to select legacy instead of UEFI and boot, and legacy Windows should be offered too.
Okay this is weird but, it shows that I already have the latest version of grub 2.02-2ubuntu18.5
But the grub menu still only shows Ubuntu and Advanced options for Ubuntu

I am now going to try the refind boot manager approach. Wil keep everybody posted.

Okay
refind could do absolutely nothing. Initially it showed only two options - boot into Ubuntu and Fallback Bootloader, both of which boot to Ubuntu (UEFI)
When I edited the refind.conf files (as mentioned in dragonfly41 's idea and the link mentioned) after mounting the  EFI partition (/boot/efi/EFI/refind/refind.conf to include the scanfor hdbios line and uefi_deep_legacy_scan, another option showed up which still booted into Ubuntu Legacy.
My best guess is that something has seriously gone wrong with my Windows installation so now I'll be clearing the whole disk and starting with a fresh dual boot.
I'm marking this thread as solved.

---

