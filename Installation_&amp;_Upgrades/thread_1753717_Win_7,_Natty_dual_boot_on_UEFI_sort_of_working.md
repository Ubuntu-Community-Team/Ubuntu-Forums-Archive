---
title: "Win 7, Natty dual boot on UEFI sort of working"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by SaryonOnline on 2011-05-09
Hello everyone,

After more than a week of fiddling (20+ hours) i finally managed to boot natty in a dual boot setup with windows 7 on a UEFI only motherboard (no fallback BIOS). I am really happy about this and could not find any how to that applied to my situation, so I'm posting this quite cumbersome manual method of booting. EDIT: only one key press still required.

I don't have much experience using grub. Previous dual boot configurations always worked automatically for me. Any comments on how to improve things are very welcome!

Situation: Asrock p67 extreme4 motherboard with UEFI. One hdd (sda) and one ssd (sdb). Windows 7 installed and boots fine. Windows created GPT partitions: sdb1 as EFS, sdb2 as MRP and sdb3 for Windows 7.

I Installed Ubuntu 11.04 on sdb4 with the bootloader on sdb1. The installer changed absolutely nothing on the boot partition, so i used the LiveCD to manually install grub there. This failed because of an error (cannot stat aufs), but using the help on the ubuntu bug 703009 page i got it working. ([https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/703009](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/703009) post 14 and 22)

I will use / to denote /dev/sdb1, the EFS partition root. My boot partition now had the following folders: /EFI/Boot, /EFI/Microsoft, /EFI/grub (all the grub files) /EFI/ubuntu (empty)

Still no grub boot option on the UEFI bootloader and booting sdb gave me just a blinking underscore.

Next thing i did was download the UEFI shell ([http://tianocore.git.sourceforge.net/git/gitweb.cgi?p=tianocore/edk2;a=blob_plain;f=EdkShellBinPkg/FullShell/X64/Shell_Full.efi;hb=HEAD](http://tianocore.git.sourceforge.net/git/gitweb.cgi?p=tianocore/edk2;a=blob_plain;f=EdkShellBinPkg/FullShell/X64/Shell_Full.efi;hb=HEAD), thanks to the archlinux forum), rename it to shellx64.efi as requested by my UEFI and put it in /, /EFI and /EFI/Boot, just to be sure. It's probably supposed to be in /.

Now to the actual booting: go into UEFI, go to the exit page and start the shell.
- type fs0:
- cd to directory containing grub.efi (EFI\grub in my case)
- type grub.efi

In grub do the following:
set root=(hd1,4) (change according to your situation)
linux /vmlinuz root=/dev/sdb4 ro (change this as well)
initrd /initrd.img
boot

This method boots my system into Ubuntu, where i can now finally catch up on a lot of work :)

There are probably two ways to automate this process:
- Install grub correctly (If anyone knows how, please let me know).
- Create a UEFI shell script to start grub and do something in grub to make it autoboot ubuntu. 

EDIT:
I fiddled around a bit and now i get a proper grub menu, though i'm not sure what exactly i did. 

The UEFI shell script works, using the script bit at the bottom of this page: [http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
The main problem I had to overcome here was getting the script to autorun. My UEFI setup has no shell option in the bootloader (no auto shell at startup, it has to be manually selected every time). To solve this I cloned the EFS partition and replaced the windows bootloader on one of them with the shell. The bootscript points to the windows files on the other partition.

I'm not sure how clear all of this is, but hopefully it saves other people some time. 

This method still requires one keypress, since I couldn't figure out how to autoselect an option in the script after a set amount of seconds. It would be much appreciated if someone can point me in the right direction here.

---

### Post by RoboJ1M on 2011-05-09
I'm going to be purchasing an Asrock UEFI mobo for a friend's PC build soon.

It's going to be running just Ubuntu 11.04 (no windows)
I'll let you know how it goes.

J.

---

### Post by SaryonOnline on 2011-05-09
I think i had just ubuntu running a while back, using MSDOS format partition tables. I switched to GPT because, as far as i know, 7 needs GPT.

Also, I now have a makeshift shellscript bootloader with options for windows, grub and the shell, but no way to autoboot it without breaking the windows bootloader.

EDIT: updated the first post with more info.

---

### Post by vm_boy on 2011-08-18
> I Installed Ubuntu 11.04 on sdb4 with the bootloader on sdb1. The installer changed absolutely nothing on the boot partition, so i used the LiveCD to manually install grub there. This failed because of an error (cannot stat aufs), but using the help on the ubuntu bug 703009 page i got it working. ([https://bugs.launchpad.net/ubuntu/+s...b2/+bug/703009](https://bugs.launchpad.net/ubuntu/+s...b2/+bug/703009) post 14 and 22)

Could you expound on this, please?  I'm not sure how to install grub on the EFI partition.

I have a 64-bit UEFI machine with Windows 7 currently installed.  I'm trying to figure out what the next step is to install Ubuntu 11.04.

My partitions are like so:
sda1 = Linux partition (not yet installed)(60 GB)
sda2 = Windows (100 GB)
sda3 = EFI (don't know how it got to sda3, but it did) (100 MB)
sda4 = Swap (4GB)
sda5+ = unallocated, but I intend to make a partition for installed Programs (~336 GB)

sdb = Documents (NTFS) (1.5TB)

sdc = External HDD (1.0 TB)

Last night, I tried to install Ubuntu on sda1 (mounted / there) and indicated sda3 as an EFI partition.  In the process, Ubuntu wiped out the Windows boot files in the EFI, but when it restarted it went straight to Ubuntu (no GRUB boot options, but at least it booted into Ubuntu).  Once it was loaded up, it updated some files and needed to restart.  Upon restart, it went to "grub rescue>", but the only functions it recognized were ls and set.  Not insmod, boot, normal, etc.

Fortunately, I had set a restore point for Windows so I restored everything up until the point where I started installing Ubuntu.  So now what should I try?

Also, I downloaded a new copy of the Ubuntu .iso and created a new USB Live disk just in case I had a faulty .iso originally.

---

### Post by ProNux on 2011-09-21
> **SaryonOnline said:**
> Hello everyone,

After more than a week of fiddling (20+ hours) i finally managed to boot natty in a dual boot setup with windows 7 on a UEFI only motherboard (no fallback BIOS). I am really happy about this and could not find any how to that applied to my situation, so I'm posting this quite .....

I want to follow your procedure on my UEFI notebook.  One thing, did you install Windows 7 first?  I know in MBR systems, it is recommended to install Windows first, then Ubuntu.

Did you use chainloading? (as described below)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by srs5694 on 2011-09-21
SaryonLinux,

I'm afraid I missed this thread earlier. You might want to try using rEFIt as your primary boot loader. The following procedure should do the trick:


[list=1]
[*]Boot Ubuntu in whatever way you can.
[*]Open a Terminal window.
[*]Type "cd /boot/efi/EFI".
[*]Type "sudo mv BOOT BOOT-backup". (In theory, you could delete the BOOT directory, since it should just contain a duplicate of another boot loader, but I want to be sure you don't delete something important if your files are a bit odd.)
[*]Type "sudo mkdir BOOT".
[*]Type "sudo apt-get install refit".
[*]Type "cd /usr/lib/refit".
[*]Type "sudo cp -r refit/* /boot/efi/EFI/BOOT".
[*]Type "sudo cp x64/refit.efi /boot/efi/EFI/BOOT/bootx64.efi".
[*]Use your favorite editor to edit the /boot/efi/EFI/BOOT/refit.conf file. Locate the line that reads "#textonly" and uncomment it by removing the "#" at the start of the line.
[/list]


This sets up rEFIt as the default boot loader; however, depending on your configuration, it could be that your system is configured to use something else (perhaps launch the EFI shell that you installed), so you might need to do some more configuration to get it running by default.

When rEFIt does run, you'll see a list of EFI boot loaders from which you can select. rEFIt also probes for and offers BIOS boot loaders; however, most or all of these will be useless on your system, so they'll clutter the boot loader display unnecessarily. (Unfortunately, there's no way to configure rEFIt to ignore them.)

---

### Post by srs5694 on 2011-09-21
> **ProNux said:**
> I want to follow your procedure on my UEFI notebook.  One thing, did you install Windows 7 first?  I know in MBR systems, it is recommended to install Windows first, then Ubuntu.

Ubuntu's installer (through at least 11.04) has the unfortunate habit of trashing the EFI System Partition (ESP; what SaryonOnline referred to as the "EFS"). The contents of this partition are vital for any OS that boots, so if you install Windows first and Ubuntu second, the result is that Windows will no longer be bootable. SayonOnline seems to have escaped this fate by manually partitioning and not identifying the EFI System Partition (ESP). This has the effect of not installing GRUB, so that Ubuntu won't boot, and SaryonOnline had to install GRUB manually.

If you install Ubuntu first and identify your ESP as such in the partitioning screen, Ubuntu creates a FAT-16 ESP. Unfortunately, Windows expects to see a FAT-32 ESP, so Windows won't install. What's more, the ESP that Ubuntu creates is tiny -- normally under 100 MiB, although I think the size varies depending on the disk size. Windows creates a 100 MiB ESP by default. For some boot loaders, an ESP of well over 100 MiB is desirable, since the Linux kernel and initial RAM disk must be stored on the ESP (or on some other partition that the EFI can read).

All of this sets up a nasty obstacle course. There are several ways to navigate it. In broad outline, the simplest way is probably:


[list=1]
[*]Boot using an emergency disc and set up GPT partitions, including a 200-300 MiB FAT32 ESP at the start of the disk and a 1 MiB [BIOS Boot Partition.](http://en.wikipedia.org/wiki/BIOS_Boot_partition)
[*]Install Windows in UEFI mode.
[*]Switch to BIOS mode and install Ubuntu.
[*]In Ubuntu (booted in BIOS mode), install an EFI-capable boot loader to the ESP.
[*]Switch the computer back to UEFI mode.
[/list]


It should now be possible to boot Windows or Ubuntu in UEFI mode, although you may need to do a bit more fiddling to get everything working completely correctly.

SaryonOnline claims that his motherboard doesn't have a BIOS fallback mode. This is the first I've heard of such a thing in a modern motherboard, although older EFI implementations lacked this feature, and it's conceivable that some modern boards lack it, too. If you lack a BIOS boot mode, or if you just want to do it the hard way, you could do this:


[list=1]
[*]Boot using an emergency disc and set up GPT partitions, including a  200-300 MiB FAT32 ESP at the start of the disk.
[*]Install Windows in UEFI mode.
[*]Boot using an emergency disc and back up the contents of the ESP. (A normal file copy to a removable disk will do fine.)
[*]Install Ubuntu in UEFI mode, being sure to point out the ESP to the installer if you do manual partitioning.
[*]When you reboot into your working Ubuntu system, restore the EFI/Microsoft directory from the ESP backup you made earlier. For extra flexibility in the future, you could back up the ESP, convert it back to FAT32, and restore everything. This will likely require editing /etc/fstab.
[*]Re-run the update-grub script. In theory, this should detect your Windows installation and add it to GRUB's menu. If not, you could install rEFIt, as described in my previous post, to use as the OS selector.
[/list]


Be aware that many people have reported problems with GRUB 2 in UEFI mode, particularly using the Ubuntu package. Thus, you may need to install it from source code yourself or use another boot loader, such as [ELILO,](http://elilo.sourceforge.net) to boot Ubuntu. ELILO can boot a Linux kernel but can't chainload to another boot loader or OS. rEFIt can chainload to another boot loader but can't load a Linux kernel directly. IMHO, the best combination of boot loaders for a dual-boot Windows/Linux UEFI computer is to use rEFIt to select the OS, ELILO to boot a Linux kernel, and the Windows EFI loader to boot the Windows kernel.

---

### Post by ProNux on 2011-09-22
@srs5694
Thanks for the detailed procedure.
I'm a bit confused on my NB right now.

1. I have a Phoenix SecureCore Tiano BIOS (which supports both UEFI & BIOS)
2.  The BIOS has no option to select if UEFI/GPT or BIOS/MBR
3. To know whether the factory settings uses UEFI/BIOS, I transfered the hard disk to my Ubuntu desktop and found out that the partitioning is MBR (by using gparted).
4.  I proceed to install Ubuntu x64 alongside Windows 7 x64 by BIOS/MBR mode.
5.  Install went fine (as I normally do on my desktop).
6.  After install, GRUB won't show up and just boots directly to Windows.
7.  @ Windows, I check the Disk manager & the Ubuntu partition/swap partition was there.
8.  I tried to reinstall both Windows 7 x64 & Ubuntu x64 on a DIFFERENT hard disk.  SAME thing happens - GRUB won't show up, instead, it boot directly to Windows.

In this wiki,
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

They said
> Some machines (all Dell laptops, all new Apple from 2010 on, some Lenovo) have bugs in their UEFI firmware, preventing them from booting (black screen). Linux Kernel 3.0 (and higher versions) includes patches with workarounds for them. It is therefore recommended to use a Linux kernel of version 3.0 or higher.

so right now, I am downloading the Ubuntu 11.10 beta with kernel 3.0 and will later know if this solves my problem.

My notebook is Fujitsu PH521.


UPDATE:
After installing Ubuntu Beta with kernel 3.0, NOTHING happens.  I have done almost all efforts for this simple task to no avail.  I have installed several dual boot OS on my PCs without problem.  Even Ubuntu-only installation (NO WINDOWS), the notebook just freezes at boot, no grub bootloader.

---

### Post by srs5694 on 2011-09-22
> **ProNux said:**
> 2.  The BIOS has no option to select if UEFI/GPT or BIOS/MBR

Based on my personal experience, reports I've read, and manuals I've read, such options are usually present in UEFI boards but are usually very poorly labelled. Check your firmware's Boot menu, or anything that might be labelled in a similar way. There may be an option relating to "legacy boot" (read: BIOS boot) or references to UEFI-specific features (such as a UEFI boot loader).

> 6.  After install, GRUB won't show up and just boots directly to Windows.

This sounds like GRUB wasn't installed, or perhaps it installed to a partition rather than to the MBR. This could happen because of a bug or because you selected an option during installation that prevented its installation to the MBR.

Your best bet is to download the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) and run it from a Linux emergency disc. It will produce a file called RESULTS.txt. Post it here, either as an attachment or between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.

> In this wiki,
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

They said

Since you're booting in BIOS mode, this is irrelevant. Furthermore, this describes a kernel issue, and since you aren't even seeing a GRUB screen, the kernel is irrelevant. (GRUB loads the kernel, so if GRUB doesn't run, the kernel can't be involved in the problem.)

---

### Post by ProNux on 2011-09-22
**@srs5694**

I managed to install & boot UBUNTU ONLY on my notebook.  I used the Startup Disk Creator on my Ubuntu desktop & USB flash drive (originally, I used unetbootin, not sure if it was related).

I'm sure there were no boot selection (UEFI or BIOS) in the Bios Menu as there were only a FEW options to change.

Here are my discoveries on my notebook. 

1. **After Ubuntu install, the partition was default to GPT!!  It was done automatically.**

   Originally when I install a fresh copy of Windows, it defaults to BIOS/MBR partitioning!!

Here I conclude (yet as of the moment) that my BIOS (Phoenix SecureCore Tiano compiled by Fujitsu) decides automatically if it will use GPT/MBR.  Correct me if I am wrong.

2.  [B]There is an ADDED item in "Boot Selection Menu" (F12).  The item added is "ubuntu", --> 1. Drive0, 2.  NETWORK, & the added item 3. ubuntu
[/B]
    Now, I tried to change the hard disk with Ubuntu with the factory hard disk where the original Windows was installed.  Checking the BIOS, the UBUNTU boot item (F12) is STILL THERE!!  OMG, where did it save that "ubuntu" boot menu selection item when I already changed the hard disk???

Does this mean the BIOS has a built-in writable memory???  How to erase it (when I might need to)???  Resetting to BIOS defaults DOES NOT erase the "ubuntu" boot item.


Actually this is my 2nd Fujitsu notebook, the first one was changed after a week I purchased (same exact model). I screwed the BIOS that time as I forced install Windows on GPT then I was faced with an infinite reboot loop at BIOS and the worst part, I cannot enter the BIOS.  Glad they replaced it.

So right now, I'm extra careful LOL.  I'll continue tomorrow.  It's already past 1:00 AM.

Wish me luck.

---

### Post by srs5694 on 2011-09-22
> **ProNux said:**
> 1. **After Ubuntu install, the partition was default to GPT!!  It was done automatically.**

   Originally when I install a fresh copy of Windows, it defaults to BIOS/MBR partitioning!!

Here I conclude (yet as of the moment) that my BIOS (Phoenix SecureCore Tiano compiled by Fujitsu) decides automatically if it will use GPT/MBR.  Correct me if I am wrong.

The firmware doesn't decide what partition table type (MBR or GPT) to use; that's at the discretion of the OS installer.

Under Windows, the choice of partition table is tied to the boot method: Windows uses MBR on BIOS boots and GPT on UEFI boots. Thus, if you successfully installed Windows to an MBR disk, it means that the installer was booted in BIOS mode.

Under Ubuntu, it's a bit more complex, and I may not know all the rules. Based on my own observations and reports I've seen, they seem to be:


[list]
[*]If the disk is already partitioned, the existing partition table type is used.
[*]If a blank disk is under a certain size (somewhere between 1 TB and 2 TB; I'm not sure of the exact cutoff) and if the computer booted in BIOS mode, the Ubuntu installer uses MBR.
[*]If a blank disk is over that size and if the computer booted in BIOS mode, the Ubuntu installer uses GPT.
[*]If the computer booted in UEFI mode, Ubuntu uses GPT on blank disks.
[/list]


Thus, the only thing that can be concluded from your observations of partition table types is that the computer booted in BIOS mode when you installed Windows. Depending on the disk size and whether it was partitioned before installation of Ubuntu, the Ubuntu installer *might* have booted in UEFI mode.

> 2.  [B]There is an ADDED item in "Boot Selection Menu" (F12).  The item added is "ubuntu", --> 1. Drive0, 2.  NETWORK, & the added item 3. ubuntu
[/B]
    Now, I tried to change the hard disk with Ubuntu with the factory hard disk where the original Windows was installed.  Checking the BIOS, the UBUNTU boot item (F12) is STILL THERE!!  OMG, where did it save that "ubuntu" boot menu selection item when I already changed the hard disk???

Does this mean the BIOS has a built-in writable memory???  How to erase it (when I might need to)???  Resetting to BIOS defaults DOES NOT erase the "ubuntu" boot item.

This evidence strongly suggests that at least one of your Ubuntu installations used UEFI mode. UEFI includes its own boot loader, with boot entries stored in flash memory on the motherboard. IIRC, when Ubuntu installs, it creates an entry called "ubuntu". Such entries can be managed from Linux using a text-mode program called efibootmgr (check its man page for details), and EFI implementations *should* provide a user interface to manage such entries, too; however, many of these are extremely limited.

---

### Post by ProNux on 2011-09-23
@srs5694

Now that I know Windows defaults to MBR and Ubuntu defaults to GPT, which would you recommend installing first?  I have the history of corrupting my BIOS (infinite loop) when I forced install Windows in GPT partition, since there was no BIOS option to explicitly select BIOS/MBR or UEFI/GPT. 

If I install Windows after Ubuntu in UEFI/GPT, it yields an error that it won't install in a GPT partition, I don't know why, forcing me to install Windows first in BIOS/MBR mode. 

I am thinking of using GRUB 1 (old version, which I know is not compatible to UEFI) with the latest Ubuntu so I can force install Ubuntu in BIOS/MBR after installing Windows.  How to make use of GRUB 1 with the latest Ubuntu in a live USB?

Current Status:
   /dev/sda1 -- fat16 -- mount point:  /boot/efi  --> automatically done during install
   /dev/sda2 -- ext4 -- mount point: /  -->  resized after install using gparted live usb to give space for Windows 7.
   (free, unpartitioned space for Windows 7 x64) 
   /dev/sda3 -- swap partition

I don't have the exact steps on installing Windows 7 next.

Still reading this article:
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

And also, how can I see the grub menu during boot of Ubuntu in UEFI.  If I successfully installed Windows, how can I select the OS at boot time?  How to select memtest & other linux headers?

---

### Post by srs5694 on 2011-09-23
> **ProNux said:**
> Now that I know Windows defaults to MBR and Ubuntu defaults to GPT, which would you recommend installing first?

It's not just that Windows *defaults* to MBR in BIOS mode, it's that Windows *will only* install to an MBR disk when booted in BIOS mode, and it *will only* install to a GPT disk when booted in UEFI mode. Microsoft locks you down in this way. Thus, when dual-booting Windows, you have to decide whether you want BIOS and MBR for both or GPT and UEFI for both. (In principle, you could switch between BIOS and UEFI modes to boot Linux, but in practice this is usually pretty awkward.)

> I have the history of corrupting my BIOS (infinite loop) when I forced install Windows in GPT partition, since there was no BIOS option to explicitly select BIOS/MBR or UEFI/GPT.

If you managed to install Windows on a GPT disk, you either did it by booting in UEFI mode or you used some sort of hack I've not heard of to do it in BIOS mode.

Also, a Basic Input/Output System (BIOS) is a type of firmware that resides in a chip on the motherboard. UEFI is another type of firmware that resides in a chip on the motherboard. Corrupting either will completely "brick" the computer -- it won't boot from *any* hard disk, optical disc, USB flash drive, or anything else. Thus, it's unlikely that you've corrupted your BIOS by trying to install Windows to a GPT disk. It's more likely that your installation put the wrong boot loader on the disk or damaged the boot process on the hard disk, but without knowing precisely what you did I can't speculate further on this. (I'm not asking for details, since this issue is rather peripheral; I just want to be clear on the terminology to avoid miscommunication.)

> If I install Windows after Ubuntu in UEFI/GPT, it yields an error that it won't install in a GPT partition, I don't know why, forcing me to install Windows first in BIOS/MBR mode.

The "why" is because of Microsoft's linking the firmware type very tightly to the partition table type.

> I am thinking of using GRUB 1 (old version, which I know is not compatible to UEFI) with the latest Ubuntu so I can force install Ubuntu in BIOS/MBR after installing Windows.  How to make use of GRUB 1 with the latest Ubuntu in a live USB?

You're thinking about this the wrong way. What you should do is to figure out your firmware's options for how to boot the installation discs, then decide on a mode (BIOS or UEFI). Be aware that, at least as of Ubuntu 11.04, Ubuntu UEFI installations create a number of obstacles that can trip up any but UEFI experts. Thus, for a dual-boot Windows/Ubuntu system, BIOS mode still works best. UEFI mode has some advantages, but given the problems you've been having, BIOS mode is likely to be best.

Thus, you should do this:


[list=1]
[*]Figure out your firmware boot options. Consult the manual and any online help you can find on the matter. If necessary, post every boot option you can find in your firmware's setup utility. (Post screen shots from a digital camera or transcribe the options *exactly*.)
[*]If your disk is currently partitioned using GPT, wipe it clean. The easiest way to do this in your state is to boot a Linux emergency disc, such as [Parted Magic,](http://partedmagic.com) that includes sgdisk, and type "sudo sgdisk -Z /dev/sda". This will erase all the MBR and GPT partitioning data on the disk.
[*]Boot the Windows installer in BIOS mode (either by disabling UEFI booting or by selecting a BIOS boot option for your installation disc when you boot the computer).
[*]Install Windows.
[*]Test that Windows boots.
[*]Boot the Ubuntu installer in BIOS mode -- again, by selecting appropriate firmware options.
[*]Install Ubuntu.
[/list]


If you follow this procedure, you should be able to get both OSes booting in BIOS mode. The key, however, is in figuring out how to select the boot options in your firmware. I cannot emphasize this enough. I realize that the manufacturers make these options about as clear as a light-year of lead, but if you don't understand how they work, you'll be groping about in the dark.

> And also, how can I see the grub menu during boot of Ubuntu in UEFI.  If I successfully installed Windows, how can I select the OS at boot time?  How to select memtest & other linux headers?

A properly installed and functioning dual-boot configuration should bring up GRUB automatically, whether you're using BIOS booting or UEFI booting. You won't see GRUB when booting the installer in BIOS mode, although the Ubuntu installer does use GRUB to boot the installer in UEFI mode.

---

### Post by ProNux on 2011-09-24
I have installed Windows in UEFI mode by manually partitioning my hard disk on a separate PC using gparted and specifying GPT.

At that time, an additional menu ("windows gpt" something like that) was added on the boot options, suggesting it was a UEFI installation.  It was the first device in boot order (I was not familiar with the efibootmgr then) and upon booting, I cannot enter BIOS (F2) so I concluded I corrupted the BIOS and faced with an infinite loop without loading windows, nor I can boot from USB or any device, even without the hard disk.  Glad they replaced my 1 week-old notebook that time.

Attached are screenshots from my BIOS.

As stated, note the "ubuntu" menu added on the last image.  I have now ubuntu-only OS in UEFI/GPT.  I can also install "Windows only" in BIOS mode by default, since there is no BIOS option to select BIOS/UEFI.

---

### Post by ProNux on 2011-09-24
More screenshots including sub-menus.

I have just seen my friend's notebook with AMIBIOS' Aptio and there you can explicitly enable UEFI booting, NOT my notebook.

I just hope Fujitsu updates the BIOS.

---

### Post by srs5694 on 2011-09-24
They've given you very few options to control the boot process! I suggest you try the following, with both the Windows and the Ubuntu installation discs:


[LIST=1]
[*]Insert the disc in the drive.
[*]Boot or reboot the computer and hit whatever key(s) you need to hit to get the firmware's boot menu or the Boot display from the last screen shot in your post #14.
[*]Review the boot options that are related to the optical disk. Post screen shots if you like.
[/LIST]


What I'm wondering is whether you might see *two* CD/DVD boot options when a UEFI-enabled disc is inserted in the drive. If so, one of them probably boots the computer in BIOS mode and the other does it in UEFI mode. If I'm right in this, then for some reason your Windows and Ubuntu installations were happening in different modes, and you want to use your boot-time options for force them both to occur in the same mode, as per my post #13 in this thread.

If you can't seem to get any suitable options in the firmware, it should be possible to force the issue by creating an Ubuntu install medium that lacks EFI support. There are several ways to do this. The simplest might be to use unetbootin to create an installation USB flash drive, provided you've got a spare USB flash drive. I can post further details if it comes to that, but for now I'm hoping to find a way to tell your firmware to boot Ubuntu in BIOS mode (or perhaps Windows in UEFI mode, although that's not as desirable at the moment).

---

### Post by ProNux on 2011-09-24
Very few options indeed.  I was thinking if the BIOS was done hastily or what.

I already erased the entire disk using Parted Magic as you suggested.  

1.  Installed Windows BIOS/MBR mode.  Verified and Windows is booting fine.
3.  With Ubuntu Natty DVD on drive, I selected DVD Boot Menu @ BIOS (F12).  No other menu (only 1 DVD drive found) as what you said possible.  I presume Ubuntu booted in UEFI mode.  See below screenshots.
4.  Continued booting @ Live DVD.
5.  Checked windows installation @ Live Ubuntu - Cannot find the Windows partition, but questionably it says my drive with Windows is GPT, or maybe because it is booted in UEFI mode (?)

--Reboot--

1.  With Windows 7 x64 DVD on drive, I selected DVD Boot Menu @ BIOS (F12).  Exactly same menus appeared when using Ubuntu Live DVD (step 3.)  Screenshots below.
2.  Windows install would continue normally.

There are two Tabs.  SAME menus would appear, be it on Ubuntu Live DVD or Windows 7 Install DVD

Will continue tomorrow, it's almost 1:00 AM.  Thanks for the support.

---

### Post by srs5694 on 2011-09-24
If I understand correctly, you've now got a clean installation of Windows, with nothing else on the disk. If so, please do the following:


[list=1]
[*]Boot the Ubuntu installer into its "live CD" mode.
[*]Open a Terminal window.
[*]Type "dmesg | grep EFI". If there's no output, or perhaps just one or two lines in which the string "EFI" appears in some other word, then you've booted in BIOS mode. If you get dozens of lines of output, many referring to memory mappings, then you've booted in UEFI mode.
[*]Type "sudo parted /dev/sda print". Post the result here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility. If the result includes a line that reads "Partition Table: gpt" then Windows installed in UEFI mode. If the result includes a line that reads "Partition Table: msdos" then Windows installed in BIOS mode.
[/list]


This diagnostic information may help you decide how to proceed. There are solutions to the problem of the computer booting the two OS installers in different modes, but details depend on precisely what's happened, so let's figure that out before going down some path based on assumptions that might or might not be accurate.

---

### Post by ProNux on 2011-09-25
Yes, I now have a fresh install of Windows & nothing else, after wiping out the disk with Parted Magic twice (in succession)

Here's the result of the fist command at the terminal @ Live USB (not Live DVD, I think it's just fine)
```
ubuntu@ubuntu:~$ dmesg | grep EFI
[    0.000000] EFI v2.00 by Phoenix Technologies Ltd.
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x0000000000054000) (0MB)
[    0.000000] EFI: mem02: type=4, attr=0xf, range=[0x0000000000054000-0x0000000000055000) (0MB)
[    0.000000] EFI: mem03: type=3, attr=0xf, range=[0x0000000000055000-0x000000000008f000) (0MB)
[    0.000000] EFI: mem04: type=10, attr=0xf, range=[0x000000000008f000-0x0000000000090000) (0MB)
[    0.000000] EFI: mem05: type=3, attr=0xf, range=[0x0000000000090000-0x00000000000a0000) (0MB)
[    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x0000000000100000-0x000000000054d000) (4MB)
[    0.000000] EFI: mem07: type=7, attr=0xf, range=[0x000000000054d000-0x0000000036570000) (864MB)
[    0.000000] EFI: mem08: type=2, attr=0xf, range=[0x0000000036570000-0x00000000372b0000) (13MB)
[    0.000000] EFI: mem09: type=7, attr=0xf, range=[0x00000000372b0000-0x000000007aff9000) (1085MB)
[    0.000000] EFI: mem10: type=2, attr=0xf, range=[0x000000007aff9000-0x00000000a4081000) (656MB)
[    0.000000] EFI: mem11: type=4, attr=0xf, range=[0x00000000a4081000-0x00000000a40a1000) (0MB)
[    0.000000] EFI: mem12: type=7, attr=0xf, range=[0x00000000a40a1000-0x00000000a40be000) (0MB)
[    0.000000] EFI: mem13: type=1, attr=0xf, range=[0x00000000a40be000-0x00000000a411e000) (0MB)
[    0.000000] EFI: mem14: type=7, attr=0xf, range=[0x00000000a411e000-0x00000000a417e000) (0MB)
[    0.000000] EFI: mem15: type=4, attr=0xf, range=[0x00000000a417e000-0x00000000a5849000) (22MB)
[    0.000000] EFI: mem16: type=7, attr=0xf, range=[0x00000000a5849000-0x00000000a5881000) (0MB)
[    0.000000] EFI: mem17: type=4, attr=0xf, range=[0x00000000a5881000-0x00000000a5883000) (0MB)
[    0.000000] EFI: mem18: type=7, attr=0xf, range=[0x00000000a5883000-0x00000000a5884000) (0MB)
[    0.000000] EFI: mem19: type=4, attr=0xf, range=[0x00000000a5884000-0x00000000a66d6000) (14MB)
[    0.000000] EFI: mem20: type=7, attr=0xf, range=[0x00000000a66d6000-0x00000000a68bf000) (1MB)
[    0.000000] EFI: mem21: type=2, attr=0xf, range=[0x00000000a68bf000-0x00000000a68c5000) (0MB)
[    0.000000] EFI: mem22: type=3, attr=0xf, range=[0x00000000a68c5000-0x00000000a6f0b000) (6MB)
[    0.000000] EFI: mem23: type=5, attr=0x800000000000000f, range=[0x00000000a6f0b000-0x00000000a6f90000) (0MB)
[    0.000000] EFI: mem24: type=5, attr=0x800000000000000f, range=[0x00000000a6f90000-0x00000000a700b000) (0MB)
[    0.000000] EFI: mem25: type=6, attr=0x800000000000000f, range=[0x00000000a700b000-0x00000000a704b000) (0MB)
[    0.000000] EFI: mem26: type=6, attr=0x800000000000000f, range=[0x00000000a704b000-0x00000000a704f000) (0MB)
[    0.000000] EFI: mem27: type=0, attr=0xf, range=[0x00000000a704f000-0x00000000a70ba000) (0MB)
[    0.000000] EFI: mem28: type=6, attr=0x800000000000000f, range=[0x00000000a70ba000-0x00000000a71c2000) (1MB)
[    0.000000] EFI: mem29: type=0, attr=0xf, range=[0x00000000a71c2000-0x00000000a71c6000) (0MB)
[    0.000000] EFI: mem30: type=6, attr=0x800000000000000f, range=[0x00000000a71c6000-0x00000000a71c8000) (0MB)
[    0.000000] EFI: mem31: type=0, attr=0xf, range=[0x00000000a71c8000-0x00000000a72c9000) (1MB)
[    0.000000] EFI: mem32: type=6, attr=0x800000000000000f, range=[0x00000000a72c9000-0x00000000a730b000) (0MB)
[    0.000000] EFI: mem33: type=0, attr=0xf, range=[0x00000000a730b000-0x00000000a731b000) (0MB)
[    0.000000] EFI: mem34: type=10, attr=0xf, range=[0x00000000a731b000-0x00000000a7354000) (0MB)
[    0.000000] EFI: mem35: type=10, attr=0xf, range=[0x00000000a7354000-0x00000000a739b000) (0MB)
[    0.000000] EFI: mem36: type=9, attr=0xf, range=[0x00000000a739b000-0x00000000a73e1000) (0MB)
[    0.000000] EFI: mem37: type=9, attr=0xf, range=[0x00000000a73e1000-0x00000000a73fb000) (0MB)
[    0.000000] EFI: mem38: type=4, attr=0xf, range=[0x00000000a73fb000-0x00000000a7e00000) (10MB)
[    0.000000] EFI: mem39: type=7, attr=0xf, range=[0x0000000100000000-0x000000023f000000) (5104MB)
[    0.000000] EFI: mem40: type=11, attr=0x8000000000000001, range=[0x00000000fed80000-0x00000000fed81000) (0MB)
[    0.000000] ACPI: UEFI 00000000a73e7000 0003E (v01 FUJ    PC       00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000a73e6000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000a73e1000 0012A (v01 FUJ    PC       00000001 PTL  00000001)
[    5.623964] fb0: EFI VGA frame buffer device
[    6.296836] EFI Variables Facility v0.08 2004-May-17
[    7.327483] fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver

```

---

### Post by ProNux on 2011-09-25
Second terminal command:
```
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA WDC WD3200BEVT-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   320GB  320GB  primary  ntfs

```

---

### Post by ProNux on 2011-09-25
Additional info at Live USB

---

### Post by srs5694 on 2011-09-25
Based on the information you've posted, Windows has installed in BIOS mode and the Ubuntu installer is booting in UEFI mode. The simplest and safest way to proceed is probably to convince Ubuntu to install in BIOS mode. I can think of several ways this *might* be done, but I can't guarantee that any of them would work, and at least one method (choosing the correct option from the firmware at boot time) seems to be impossible, given the information on your firmware options you've posted.

My first suggestion is this:


[list=1]
[*]If you don't already have one, obtain a USB flash drive. If you've got one that has important data, back up the data.
[*]Use [unetbootin](http://unetbootin.sourceforge.net/) to create a bootable USB flash drive from your Ubuntu installation disc.
[*]Boot with the unetbootin-created flash drive. Select the "try Ubuntu before installing" option (or whatever it's called).
[*]Check the "dmesg | grep EFI" output. If it produces no output, go ahead and install Linux and ignore the remaining steps in this procedure. If it produces the sort of output you posted earlier, continue with the remaining steps in this procedure.
[*]Remove the efi directory tree from the unetbootin USB drive. (It should contain one subdirectory and one file, efi/boot/bootx64.efi.)
[*]Reboot with the USB flash drive and check the "dmesg | grep EFI" output again. If it produces no output, proceed with installation in the normal way.
[/list]


I have other ideas for things you can try, but for now I recommend you try this.

---

### Post by ProNux on 2011-09-26
1.  Windows 7 in BIOS/MBR working fine
2.  Boot at Live USB Ubuntu Natty using unetbootin

Issuing ```
dmesg | grep EFI
``` @ live USB yielded to many memory addresses, so I continued to step 5 based on your post above, hence
3.  Poweroff
4.  Deleted the EFI directory on the live USB
5.  Booted at Live USB again.  Issuing the ```
dmesg | grep EFI
```
    yielded no more long memory addresses.
6.  Installed Ubuntu alongside preexisting Windows.  Now it detected the Windows partition, great.  Install went fine.
7.  Reboot after successful install.  Infinite loop at post, no grub menu.
8.  Boot at Live USB. Issuing ```
dmesg | grep EFI
```, see image attached., along with gparted screenshot.

It might be time to our next solution (?)

NOTE:  I did not create a swap partition.  I plan to create a swap file instead after successful install.

Extra:
Out of curiosity, I removed Windows, installed Ubuntu (without the EFI folder):  Infinite loop at POST.

---

### Post by ProNux on 2011-09-26
The way I understand it, BIOS assumed Ubuntu was installed in UEFI/GPT partition, unlike Windows.  I think there must be some workaround on the GRUB menu.

UPDATE:  Installed Ubuntu 10.04 LTS (no Windows).  Same result:  INFINITE loop at POST.  Just a recap, I can install Natty on UEFI mode (No Windows) and RUNS fine, BUT NO GRUB MENU at startup.

I think I'm gonna trim down my problem.  How can I install Ubuntu in BIOS/MBR MODE (without windows)?  I think if I can solve this problem, I can make the Dual Boot easily.

---

### Post by srs5694 on 2011-09-26
It's not clear to me what your current state is, but I recommend this:


[list=1]
[*]Get the system to a state with Windows and Ubuntu both installed in BIOS mode. Presumably neither will be bootable, but Windows will have been bootable before you installed Ubuntu. (Sorry if this makes it more work for you, but we need to either get to this point and fix it or abandon this approach and start from scratch.)
[*]Boot the Ubuntu installer into its "live CD" feature, preferably in BIOS mode. 
[*]Download the [Boot Info Script.](http://sourceforge.net/projects/bootinfoscript/)
[*]Run the Boot Info Script using sudo. (I believe it's "sudo ./bootinfoscript" to do this from the directory in which you download it.)
[*]The script should produce a file called RESULTS.txt. Post that output file here.
[/list]


This procedure should produce detailed information on your partitions and boot loader configuration. It may provide a useful clue about what's wrong -- for instance, an improperly-installed GRUB or a damaged partition or filesystem. (I'm suspicious of filesystem damage, given that your GParted output shows "unknown" as the filesystem on /dev/sda5 -- but perhaps you left that without a filesystem intentionally.)

Once you run this script and post the results, *do not* mess with the system any more. If I or somebody else recommends a fix at that point but you've changed things, the fix might fail because of intervening changes.

Also, I have a question: How are you installing Windows? Specifically, are you using a Windows recovery disc set provided by the manufacturer or by running a program from Windows to create the recovery discs; or are you using a retail DVD? This is important because a recovery disc set might lack UEFI boot support, which could be why Windows is installing in BIOS mode but Ubuntu is installing in UEFI mode. One possible way to fix this thing (albeit in the "start from scratch" category) is to install both OSes in UEFI mode, but to do that you've got to find a way to install Windows in UEFI mode, which is why I want to know how you're installing Windows.

---

### Post by ProNux on 2011-09-26
Don't worry about my current state, I have an experimental hard disk and I can format it anytime (with 3 USB flash disks of various capacities and a bunch of Linux ISOs from Ubuntu to Linux Mint to Fedora x64 and Windows bootable USB). LOL.

I can start with any state.  Now my hard disk is empty and I always make it a habit of erasing using Parted Magic (sgdisk -Z /dev/sda command).

I will try your suggestion tomorrow when I got home, it's almost 1 AM.  Thanks again.

Regarding your inquiry:
1. The /dev/sda5 was intentionally left unformatted
2. I use a bootable USB for installing Windows 7 x64 made from a Windows 7 x64 disk.  I'm not sure if it lacked UEFI support.  I don't use my OEM Windows installation.  In fact the original hard disk was set aside.  I'm not sure if the procedure in making a bootable Windows install USB is important in my case.  I found that somewhere in the internet.  All I remember was I made the USB bootable, then I copy all the contents of the Windows DVD.  And it worked.

---

### Post by srs5694 on 2011-09-26
> **ProNux said:**
> Regarding your inquiry:
1. The /dev/sda5 was intentionally left unformatted
2. I use a bootable USB for installing Windows 7 x64 made from a Windows 7 x64 disk.  I'm not sure if it lacked UEFI support.  I don't use my OEM Windows installation.  In fact the original hard disk was set aside.

OK, thanks. My last suggestion for how to proceed still stands, but the way you're booting Windows might explain why you can't install it in UEFI mode, since the supported methods for launching a UEFI boot loader differ a bit from one boot method to another. If it comes to it, there are ways around this.

---

### Post by ProNux on 2011-09-26
> **srs5694 said:**
> OK, thanks. My last suggestion for how to proceed still stands, but the way you're booting Windows might explain why you can't install it in UEFI mode, since the supported methods for launching a UEFI boot loader differ a bit from one boot method to another. If it comes to it, there are ways around this.

I will find out if my Windows installer has UEFI support.  Have to google it.  Or is there a quick check?

---

### Post by srs5694 on 2011-09-26
> **ProNux said:**
> I will find out if my Windows installer has UEFI support.  Have to google it.  Or is there a quick check?

Since you say you "set aside" your original hard disk, you could see whether it uses an MBR or a GPT configuration. If it's GPT, then that means that Windows was installed to it in UEFI mode, and presumably the install discs you could create from it would support UEFI installations. An MBR result would be more ambiguous, since it could be that the discs would support both modes, even though the manufacturer chose to use BIOS mode.

---

### Post by ProNux on 2011-09-26
> **srs5694 said:**
> Since you say you "set aside" your original hard disk, you could see whether it uses an MBR or a GPT configuration. If it's GPT, then that means that Windows was installed to it in UEFI mode, and presumably the install discs you could create from it would support UEFI installations. An MBR result would be more ambiguous, since it could be that the discs would support both modes, even though the manufacturer chose to use BIOS mode.
I just checked the OEM install of Windows on the original hard drive.  And using the same commands on Live USB, Windows was installed in BIOS/MBR mode; Live USB boots in UEFI mode.

---

### Post by ProNux on 2011-09-27
> **srs5694 said:**
> It's not clear to me what your current state is, but I recommend this:


[list=1]
[*]Get the system to a state with Windows and Ubuntu both installed in BIOS mode. Presumably neither will be bootable, but Windows will have been bootable before you installed Ubuntu. (Sorry if this makes it more work for you, but we need to either get to this point and fix it or abandon this approach and start from scratch.)

If I don't delete the "EFI" folder on the Live USB and install it side by side with Windows: Windows will boot / no GRUB menu / Ubuntu cannot boot, but partition is intact.

---

### Post by ProNux on 2011-09-27
> **srs5694 said:**
> Run the Boot Info Script using sudo. (I believe it's "sudo ./bootinfoscript" to do this from the directory in which you download it.)
[*]The script should produce a file called RESULTS.txt. Post that output file here.
[/list]

I followed the procedure here:
[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")
Error:  No such file or directory.

Searched the net I saw this topic.  Seems there is a bug in Natty.
[http://ubuntuforums.org/showthread.php?t=1676235&page=14]("http://ubuntuforums.org/showthread.php?t=1676235&page=14")

I will try to boot Live at Ubuntu Lucid.

---

### Post by ProNux on 2011-09-27
Current State:
1. Installed Windows 7; confirmed working
2. DID NOT REMOVE "EFI" folder in Natty Live USB
3. Installed Natty alongside Windows 7
4. Reboot.  NO GRUB Menu.  Proceeds to boot Windows like there is no other OS installed.
4. Boot at "LUCID LYNX" Live USB (Due to Natty boot script bug)
5. Result below.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 7390096 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   125,829,119   125,622,272   7 NTFS / exFAT / HPFS
/dev/sda3         125,831,166   625,141,759   499,310,594   5 Extended
/dev/sda5         125,831,168   609,200,127   483,368,960  83 Linux
/dev/sda6         609,202,176   625,141,759    15,939,584  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,826,383     7,826,322   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CEBAD848BAD82F29                       ntfs       System Reserved
/dev/sda2        041A4F051A4EF2EA                       ntfs       
/dev/sda5        283dec49-7d7e-4e40-8109-76e093551ed2   ext4       
/dev/sda6        7d751e0b-ef91-4360-8ed3-204895ba2136   swap       
/dev/sdb1        D87B-2965                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 283dec49-7d7e-4e40-8109-76e093551ed2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 283dec49-7d7e-4e40-8109-76e093551ed2
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 283dec49-7d7e-4e40-8109-76e093551ed2
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=283dec49-7d7e-4e40-8109-76e093551ed2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 283dec49-7d7e-4e40-8109-76e093551ed2
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=283dec49-7d7e-4e40-8109-76e093551ed2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 283dec49-7d7e-4e40-8109-76e093551ed2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 283dec49-7d7e-4e40-8109-76e093551ed2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root CEBAD848BAD82F29
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=283dec49-7d7e-4e40-8109-76e093551ed2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7d751e0b-ef91-4360-8ed3-204895ba2136 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 104.126224518 = 111.804682240  boot/grub/grub.cfg                             1
  60.155155182 = 64.591106048   boot/initrd.img-2.6.38-8-generic               2
 202.131351471 = 217.036886016  boot/vmlinuz-2.6.38-8-generic                  1
  60.155155182 = 64.591106048   initrd.img                                     2
 202.131351471 = 217.036886016  vmlinuz                                        1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32

prompt 0

menu title UNetbootin

timeout 100



label unetbootindefault

menu label Default

kernel /ubnkern

append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --



label ubnentry0

menu label ^Help

kernel /ubnkern

append initrd=/ubninit 



label ubnentry1

menu label ^Try Ubuntu without installing

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --



label ubnentry2

menu label ^Install Ubuntu

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --



label ubnentry3

menu label ^Check disc for defects

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --



label ubnentry4

menu label Test ^memory

kernel /install/mt86plus

append initrd=/ubninit 



label ubnentry5

menu label ^Boot from first hard disk

kernel /ubnkern

append initrd=/ubninit 



--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 


```

---

### Post by srs5694 on 2011-09-27
OK, try this:


[list=1]
[*]Ensure that your computer is connected to a network (you may need network access for this to work).
[*]Boot using the Ubuntu installer in its "try Ubuntu without installing" mode.
[*]Open a Terminal window and type the following commands:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt

```
[*]Type "apt-get install grub-pc". This is where this procedure is most likely to fail. If it tells you that grub-pc is already the latest version, it's fine. If it replaces grub-efi-amd64 with grub-pc, it's fine. If it attempts such a replacement but fails, then there's a problem with the network configuration or some other issue. If you get errors that you don't understand, post them here.
[*]Type "grub-install /dev/sda".
[*]Type "exit".
[*]Type "sudo reboot". The computer should do a few things, then prompt you to remove the installation media. Do so. When you press Enter, it should reboot into GRUB.
[/list]


If this doesn't work, try re-running the Boot Info Script and post the new results.

---

### Post by ProNux on 2011-09-27
Do I need to do the above with my current state?  By the way, any network will do?  I am connected to an internet like this:

Option 1:  Notebook --> LAN --> Router (connected as Client Bridge) --> Internet (WiFi)
Option 2:  Notebook --> WLAN --> Router (connected as Client Bridge) --> Internet (WiFi)

EDIT:  I missed this one.  You mean connected to the internet because of the "apt-get install" command.  Got it.

---

### Post by srs5694 on 2011-09-27
> **ProNux said:**
> Do I need to do the above with my current state?

Yes.

---

### Post by ProNux on 2011-09-28
Followed your instructions well.

> **srs5694 said:**
> OK, try this:
Type "grub-install /dev/sda".


A graphical menu appeared (2nd image below) before the command above, so I selected /dev/sda  , I believe it did just like the command above.

I got infinite loop at POST and Windows cannot boot.  See attached screenshots.

Also attached are the results in the Terminal when I was following your procedure (pasted to text editor) & the NEW Boot Info Script result.

By the way, I got the Boot Info Script to work in Natty, so now I used Natty Live USB (Not Lucid anymore as stated in Post #32)

---

### Post by ProNux on 2011-09-28
Terminal results & Boot Info Script Result attached.
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........;.8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 7380432 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   125,829,119   125,622,272   7 NTFS / exFAT / HPFS
/dev/sda3         125,831,166   625,141,759   499,310,594   5 Extended
/dev/sda5         125,831,168   609,200,127   483,368,960  83 Linux
/dev/sda6         609,202,176   625,141,759    15,939,584  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,826,383     7,826,322   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        04AC0DA3AC0D907A                       ntfs       System Reserved
/dev/sda2        9EEE21D4EE21A60D                       ntfs       
/dev/sda5        a77b7d68-337c-488e-a898-9cdb5e067a8f   ext4       
/dev/sda6        cbf18d8f-5ca7-46ee-a52a-96055e004f85   swap       
/dev/sdb1        7828-AC3A                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root a77b7d68-337c-488e-a898-9cdb5e067a8f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root a77b7d68-337c-488e-a898-9cdb5e067a8f
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a77b7d68-337c-488e-a898-9cdb5e067a8f
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a77b7d68-337c-488e-a898-9cdb5e067a8f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a77b7d68-337c-488e-a898-9cdb5e067a8f
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a77b7d68-337c-488e-a898-9cdb5e067a8f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a77b7d68-337c-488e-a898-9cdb5e067a8f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a77b7d68-337c-488e-a898-9cdb5e067a8f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a77b7d68-337c-488e-a898-9cdb5e067a8f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cbf18d8f-5ca7-46ee-a52a-96055e004f85 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 184.136604309 = 197.715173376  boot/grub/core.img                             1
 148.175495148 = 159.102226432  boot/grub/grub.cfg                             1
  61.165039062 = 65.675460608   boot/initrd.img-2.6.38-8-generic               2
 184.133792877 = 197.712154624  boot/vmlinuz-2.6.38-8-generic                  1
  61.165039062 = 65.675460608   initrd.img                                     2
 184.133792877 = 197.712154624  vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by srs5694 on 2011-09-28
I've heard of GRUB creating infinite loop problems like this before, but I don't know what the solution might be. I recommend you create a new thread with the Boot Info Script output, as complete a description of what you see during the infinite loop as possible (especially whether you see the word "GRUB" appear at any time), and a title like "GRUB infinite loop problem". With any luck that will catch the attention of those who might know the solution.

I have two other ideas for possible avenues to explore:


[list]
[*]Keep the current partitions and installations but replace GRUB 2 with GRUB Legacy or even LILO. These older boot loaders might not suffer from whatever problem is causing your system to reboot in this way.
[*]Start from scratch, this time finding a way to get Windows to install in UEFI mode. I'd like to hold off on this attempt, since fixing your current GRUB problem is likely to be easier than overcoming a fresh set of problems.
[/list]

---

### Post by srs5694 on 2011-09-28
Actually, I just had an idea you might try:


[list=1]
[*]Download and burn the [Super GRUB 2 Disk.](http://www.supergrubdisk.org/)
[*]Boot with the Super GRUB 2 Disk. It will give you a list of options to locate systems. You may need to try a few options before you find one that loads your current GRUB installation. With any luck, though, it will successfully boot your Ubuntu installation.
[*]Remove the Super GRUB 2 Disk from the system.
[*]Open a Terminal and type "sudo grub-install /dev/sda" to re-install GRUB.
[*]Reboot to test it.
[/list]

---

### Post by ProNux on 2011-09-28
How about installing GRUB in all partitions?  Or is this futile?

---

### Post by srs5694 on 2011-09-28
> **ProNux said:**
> How about installing GRUB in all partitions?  Or is this futile?

That's not likely to be helpful, and depending on what you mean by "all partitions," it could be damaging. As a general rule, GRUB 2 works best when it's installed to the MBR. It *can be* installed to a Linux partition's boot record, but then it needs something else to chainload to it. Given the way your disk is partitioned, the Windows boot loader can't do that, although changing /dev/sda5 to a primary partition would enable this configuration. It's unclear that such a change would be effective, and it might be disruptive. Thus, I suggest you try with Super GRUB 2 Disk before trying to reconfigure GRUB in a more fundamental way.

---

### Post by ProNux on 2011-09-28
> **srs5694 said:**
> Actually, I just had an idea you might try:


[list=1]
[*]Download and burn the [Super GRUB 2 Disk.](http://www.supergrubdisk.org/)
[*]Boot with the Super GRUB 2 Disk. It will give you a list of options to locate systems. You may need to try a few options before you find one that loads your current GRUB installation. With any luck, though, it will successfully boot your Ubuntu installation.
[*]Remove the Super GRUB 2 Disk from the system.
[*]Open a Terminal and type "sudo grub-install /dev/sda" to re-install GRUB.
[*]Reboot to test it.
[/list]
I think I can try this now, seems I can do it quickly.

---

### Post by ProNux on 2011-09-28
> **srs5694 said:**
> Actually, I just had an idea you might try:


[list=1]
[*]Download and burn the [Super GRUB 2 Disk.](http://www.supergrubdisk.org/)
[*]Boot with the Super GRUB 2 Disk. It will give you a list of options to locate systems. You may need to try a few options before you find one that loads your current GRUB installation. With any luck, though, it will successfully boot your Ubuntu installation.
[*]Remove the Super GRUB 2 Disk from the system.
[*]Open a Terminal and type "sudo grub-install /dev/sda" to re-install GRUB.
[*]Reboot to test it.
[/list]
Infinite loop at POST at Step 2, so I cannot proceed to the next step.  Burnt the disc twice to verify image was successfully burnt.  Same result.
It appears as if my BIOS rejects GRUB 2.

---

### Post by oldfred on 2011-09-28
Since it looks difficult to solve can we try an experiment. I have had this work on 2 users and not work on at least one.

Shrink Linux sda5 partition to 25GB and reinstall grub2's boot loader.

The issue has appeared more on 500Gb and larger drives with newer BIOS that seem to behave like the old BIOS issue with only being able to boot from the first 137GB of a drive. I believe their must be a BIOS setting that is contributing to the issue but do not know answer.

#Comments are anything after the #, enter commands in terminal session, be sure to use LiveCD that is same version as your install.
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
 
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by ProNux on 2011-09-28
> **srs5694 said:**
> That's not likely to be helpful, and depending on what you mean by "all partitions," it could be damaging. As a general rule, GRUB 2 works best when it's installed to the MBR. It *can be* installed to a Linux partition's boot record, but then it needs something else to chainload to it. Given the way your disk is partitioned, the Windows boot loader can't do that, although changing /dev/sda5 to a primary partition would enable this configuration. It's unclear that such a change would be effective, and it might be disruptive. Thus, I suggest you try with Super GRUB 2 Disk before trying to reconfigure GRUB in a more fundamental way.

I'm still looking forward to this chainloading option with GRUB installed on the Linux partition.  I'm willing to solve this problem with the help of you & the community.  My hard disk is now dedicated for experiments.  I will try to create a new thread tomorrow, but I like to keep this thread active.

I will try your above suggestion tomorrow again.  Thanks.

---

### Post by ProNux on 2011-09-28
> **oldfred said:**
> Since it looks difficult to solve can we try an experiment. I have had this work on 2 users and not work on at least one.

Shrink Linux sda5 partition to 25GB and reinstall grub2's boot loader.

The issue has appeared more on 500Gb and larger drives with newer BIOS that seem to behave like the old BIOS issue with only being able to boot from the first 137GB of a drive. I believe their must be a BIOS setting that is contributing to the issue but do not know answer.

#Comments are anything after the #, enter commands in terminal session, be sure to use LiveCD that is same version as your install.
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
 Infinite loop at post at this point after reboot.
Cannot proceed to the last step as below
```
sudo update-grub
```

Reboot at live USB.  Run boot info script.  Results as attached.
```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........;.8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 7380432 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   125,829,119   125,622,272   7 NTFS / exFAT / HPFS
/dev/sda3         125,831,166   625,141,759   499,310,594   5 Extended
/dev/sda5         125,831,168   177,031,167    51,200,000  83 Linux
/dev/sda6         609,202,176   625,141,759    15,939,584  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,826,383     7,826,322   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        04AC0DA3AC0D907A                       ntfs       System Reserved
/dev/sda2        9EEE21D4EE21A60D                       ntfs       
/dev/sda5        a77b7d68-337c-488e-a898-9cdb5e067a8f   ext4       
/dev/sda6        cbf18d8f-5ca7-46ee-a52a-96055e004f85   swap       
/dev/sdb1        7828-AC3A                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root a77b7d68-337c-488e-a898-9cdb5e067a8f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root a77b7d68-337c-488e-a898-9cdb5e067a8f
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a77b7d68-337c-488e-a898-9cdb5e067a8f
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a77b7d68-337c-488e-a898-9cdb5e067a8f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a77b7d68-337c-488e-a898-9cdb5e067a8f
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a77b7d68-337c-488e-a898-9cdb5e067a8f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a77b7d68-337c-488e-a898-9cdb5e067a8f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root a77b7d68-337c-488e-a898-9cdb5e067a8f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a77b7d68-337c-488e-a898-9cdb5e067a8f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cbf18d8f-5ca7-46ee-a52a-96055e004f85 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  62.230033875 = 66.818990080   boot/grub/core.img                             1
  60.211025238 = 64.651096064   boot/grub/grub.cfg                             1
  61.165039062 = 65.675460608   boot/initrd.img-2.6.38-8-generic               2
  61.143886566 = 65.652748288   boot/vmlinuz-2.6.38-8-generic                  1
  61.165039062 = 65.675460608   initrd.img                                     2
  61.143886566 = 65.652748288   vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by srs5694 on 2011-09-28
This one's really weird, and although I know a thing or two about GRUB, the infinite reboot symptom is quite peculiar. If you'd like to continue with this avenue and post another thread, that's fine. The other two alternatives I can see, which I outlined in post #39, are:

[quote=srs5694]

[LIST]
[*]Keep the current partitions and installations but replace GRUB 2  with GRUB Legacy or even LILO. These older boot loaders might not  suffer from whatever problem is causing your system to reboot in this  way.
[*]Start from scratch, this time finding a way to get Windows to  install in UEFI mode. I'd like to hold off on this attempt, since fixing  your current GRUB problem is likely to be easier than overcoming a  fresh set of problems.[/quote]
[/LIST]
I just checked, and Ubuntu does include a both a GRUB legacy package ("grub") and a LILO package ("lilo"), so swapping one of those in should be possible, although you'll need to do so with an emergency disk and perhaps a chroot environment, such as I described in post #34.

For the other option, getting Windows installed in UEFI mode is likely to require some trickery, but it should be possible. I've got several ideas for how to do this if it comes to it, but I can't guarantee that any one method would work.

---

### Post by oldfred on 2011-09-28
It would be best to completely purge grub2 if installing grub legacy. Kansasnoob's post is a one line version (change to sda5) of chroot which is easy to paste. Uses && to combine lines.

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

It is similar to purging and installing grub2 except you install grub, not grub-pc. You have to reinstall grub common in all cases.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

---

### Post by ProNux on 2011-09-29
I will do the above and will post the results soon.  I think this is a real challenge for an average user like me, and may be for some UEFI experts.

By the way, I contacted my notebook support.  An excerpt from their reply below:

*"Thanks for the reply. For your request to boot into UEFI mode, sorry to inform you that our current BIOS do not implement this features but we will feedback this to our factory side to explore for future models or BIOS update."*

But how come I can boot Natty live in UEFI mode (no dual boot), and I can even install, albeit there is no GRUB shown after POST?  So I really doubt if Fujitsu intended that way or they did it hastily?

---

### Post by ProNux on 2011-09-29
> **oldfred said:**
> It would be best to completely purge grub2 if installing grub legacy. Kansasnoob's post is a one line version (change to sda5) of chroot which is easy to paste. Uses && to combine lines.

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

It is similar to purging and installing grub2 except you install grub, not grub-pc. You have to reinstall grub common in all cases.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
Before I revert to grub legacy with my current status, since I have Ubuntu 10.04 LTS with me, I did a clean install on my hard disk of 10.04 LTS (no dual boot).  Result is "infinite loop" at POST; NO GRUB menu.  Checking on the internet, grub version for 10.04 LTS is 1.98.  Any significance / conclusions derived from my test?

UPDATE:
Just found an info.  GRUB 2 is already the default GRUB version since Karmic.  I thought at first, Lucid is using GRUB 1.  Gotta try reverting to GRUB 1 tomorrow.  Time to sleep at the moment.

---

### Post by oldfred on 2011-09-29
If the infinite boot is before grub or grub2 loads that would be BIOS related or something in hardware. It may not see hard drive, does BIOS show it correctly. LiveCD would not show hard drive if BIOS does not see it.

Do you still have boot flag on a primary partition.

I have saved a bunch of comments where BIOS was an issue, some obviously do not apply, but maybe soemething does??

Some issues on booting install:
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive
BIOS setting, Keyboard response in grub really slow

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79

---

### Post by ProNux on 2011-09-29
Unfortunately, my notebooks's BIOS has VERY FEW options to change.  You can check the entire BIOS screenshots on post #14 & 15.  The only sensible adjustment is Enabling/Disabling SATA controller & AHCI - which I tend to believe BIOS has some kind of "identity crisis" whether it is UEFI or not.

Fujitsu said they don't implement UEFI in their BIOS, but all the other information I read on the internet points out that Phoenix SecureCore Tiano is UEFI capable & is backward compatible to BIOS/MBR.  I can even boot  install Natty (no dual boot), albeit there is no grub showup after POST, just loads Natty directly.  And a new "BOOT OPTION" entry named "ubuntu" appeared on the BIOS, suggesting that Natty was installed in UEFI/GPT.

Here's what happens when I power up.
1.  Shows OEM logo.
2.  Logo stays a little longer about 6 seconds (normally only 2 to 3 seconds when only Windows x64 is installed)
3.  Auto-reboot, back to step 1.

I have not tried with USB keyboard & mouse though & other items.  I will try when I got home.  Thanks.

---

### Post by ProNux on 2011-09-30
I tried to follow the procedure in reverting Grub2 to Grub1.
[http://ubuntuforums.org/showthread.php?p=11299003#post11299003]("http://ubuntuforums.org/showthread.php?p=11299003#post11299003")

Already finished Natty install and still has not reboot yet. I don't want to reboot since grub does not show up and will just boot Windows instead.
Normally, if I follow the procedure, the /boot/grub directory points to the Live USB, not the actual Linux partition that I just installed. I tried to change the address of the ```
/boot/grub
``` to something like ```
/media/449b8b9e-027d-4272-9382-dc04fb43661/boot/grub
``` to point to my Linux partition but I got errors.

QUESTION:
1. Is it possible to revert Grub2 to Grub1 while I am at Live USB?

2. If I revert Grub2 (UEFI install) to Grub 1, does it automatically change to BIOS/MBR mode?

---

### Post by oldfred on 2011-09-30
I do not really know UEFI, but that is controlled by the UEFI/BIOS boot before you get to grub or grub2. Ubuntu's grub as I understand it was not modified to work with UEFI.

To get grub legacy to install correctly you have to follow the chroot procedure which transfers control of your LiveCD booted kernel to the system you chroot (CHange ROOT) into.

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

---

### Post by ProNux on 2011-09-30
At this point, I removed Windows.I manually created an MBR partition on the hard disk by physically connecting it to my desktop PC and put bak the hard disk on my notebook and installed Natty alone, no Windows.

After first reboot, I ended up infinite loop at POST, NO GRUB menu.

Booted on Natty Live USB.

I've mounted the linux partition and used "chroot"

I got an error, see the last line.
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ clear
















ubuntu@ubuntu:~$ ls /boot
abi-2.6.38-8-generic     memtest86+_multiboot.bin
config-2.6.38-8-generic  System.map-2.6.38-8-generic
grub                     vmcoreinfo-2.6.38-8-generic
memtest86+.bin
ubuntu@ubuntu:~$ ls /boot/grub
gfxblacklist.txt  grubenv
ubuntu@ubuntu:~$ sudo mv /boot/grub /boot/grub_backup
ubuntu@ubuntu:~$ sudo mkdir /boot/grub
ubuntu@ubuntu:~$ ls /boot
abi-2.6.38-8-generic     grub_backup               System.map-2.6.38-8-generic
config-2.6.38-8-generic  memtest86+.bin            vmcoreinfo-2.6.38-8-generic
grub                     memtest86+_multiboot.bin
ubuntu@ubuntu:~$ ls /boot/grub
ubuntu@ubuntu:~$ sudo apt-get --purge remove startupmanager
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$ sudo apt-get --purge remove startupmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package startupmanager
ubuntu@ubuntu:~$ sudo apt-get --purge remove grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-gfxpayload-lists* grub-pc*
0 upgraded, 0 newly installed, 3 to remove and 256 not upgraded.
After this operation, 7,803 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 134325 files and directories currently installed.)
Removing grub-gfxpayload-lists ...
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
ubuntu@ubuntu:~$ sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common
Suggested packages:
  grub-legacy-doc mdadm multiboot-doc grub-emu xorriso
The following NEW packages will be installed:
  grub grub-common
0 upgraded, 2 newly installed, 0 to remove and 256 not upgraded.
Need to get 2,850 kB of archives.
After this operation, 6,947 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ natty/main grub-common amd64 1.99~rc1-13ubuntu3 [2,043 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ natty/main grub amd64 0.97-29ubuntu61 [807 kB]
Fetched 2,850 kB in 21s (134 kB/s)                                             
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 134009 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.99~rc1-13ubuntu3_amd64.deb) ...
Selecting previously deselected package grub.
Unpacking grub (from .../grub_0.97-29ubuntu61_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up grub-common (1.99~rc1-13ubuntu3) ...
Setting up grub (0.97-29ubuntu61) ...
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee367556

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3917    31457280   83  Linux

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093ad3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3913161    b  W95 FAT32
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.


```


Issuing the command, as below, showed that Live USB booted in UEFI mode.```
ubuntu@ubuntu:~$ dmesg | grep EFI
[    0.000000] EFI v2.00 by Phoenix Technologies Ltd.
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x0000000000054000) (0MB)
[    0.000000] EFI: mem02: type=4, attr=0xf, range=[0x0000000000054000-0x0000000000055000) (0MB)
[    0.000000] EFI: mem03: type=3, attr=0xf, range=[0x0000000000055000-0x000000000008f000) (0MB)
[    0.000000] EFI: mem04: type=10, attr=0xf, range=[0x000000000008f000-0x0000000000090000) (0MB)
[    0.000000] EFI: mem05: type=3, attr=0xf, range=[0x0000000000090000-0x00000000000a0000) (0MB)
[    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x0000000000100000-0x000000000054d000) (4MB)
[    0.000000] EFI: mem07: type=7, attr=0xf, range=[0x000000000054d000-0x0000000036570000) (864MB)
[    0.000000] EFI: mem08: type=2, attr=0xf, range=[0x0000000036570000-0x00000000372b0000) (13MB)
[    0.000000] EFI: mem09: type=7, attr=0xf, range=[0x00000000372b0000-0x000000007affa000) (1085MB)
[    0.000000] EFI: mem10: type=2, attr=0xf, range=[0x000000007affa000-0x00000000a4081000) (656MB)
[    0.000000] EFI: mem11: type=4, attr=0xf, range=[0x00000000a4081000-0x00000000a40a1000) (0MB)
[    0.000000] EFI: mem12: type=7, attr=0xf, range=[0x00000000a40a1000-0x00000000a40bd000) (0MB)
[    0.000000] EFI: mem13: type=1, attr=0xf, range=[0x00000000a40bd000-0x00000000a411d000) (0MB)
[    0.000000] EFI: mem14: type=7, attr=0xf, range=[0x00000000a411d000-0x00000000a417d000) (0MB)
[    0.000000] EFI: mem15: type=4, attr=0xf, range=[0x00000000a417d000-0x00000000a5848000) (22MB)
[    0.000000] EFI: mem16: type=7, attr=0xf, range=[0x00000000a5848000-0x00000000a587e000) (0MB)
[    0.000000] EFI: mem17: type=4, attr=0xf, range=[0x00000000a587e000-0x00000000a66d6000) (14MB)
[    0.000000] EFI: mem18: type=7, attr=0xf, range=[0x00000000a66d6000-0x00000000a68bf000) (1MB)
[    0.000000] EFI: mem19: type=2, attr=0xf, range=[0x00000000a68bf000-0x00000000a68c5000) (0MB)
[    0.000000] EFI: mem20: type=3, attr=0xf, range=[0x00000000a68c5000-0x00000000a6f0b000) (6MB)
[    0.000000] EFI: mem21: type=5, attr=0x800000000000000f, range=[0x00000000a6f0b000-0x00000000a6f90000) (0MB)
[    0.000000] EFI: mem22: type=5, attr=0x800000000000000f, range=[0x00000000a6f90000-0x00000000a700b000) (0MB)
[    0.000000] EFI: mem23: type=6, attr=0x800000000000000f, range=[0x00000000a700b000-0x00000000a704b000) (0MB)
[    0.000000] EFI: mem24: type=6, attr=0x800000000000000f, range=[0x00000000a704b000-0x00000000a704f000) (0MB)
[    0.000000] EFI: mem25: type=0, attr=0xf, range=[0x00000000a704f000-0x00000000a70ba000) (0MB)
[    0.000000] EFI: mem26: type=6, attr=0x800000000000000f, range=[0x00000000a70ba000-0x00000000a71c2000) (1MB)
[    0.000000] EFI: mem27: type=0, attr=0xf, range=[0x00000000a71c2000-0x00000000a71c6000) (0MB)
[    0.000000] EFI: mem28: type=6, attr=0x800000000000000f, range=[0x00000000a71c6000-0x00000000a71c8000) (0MB)
[    0.000000] EFI: mem29: type=0, attr=0xf, range=[0x00000000a71c8000-0x00000000a72c9000) (1MB)
[    0.000000] EFI: mem30: type=6, attr=0x800000000000000f, range=[0x00000000a72c9000-0x00000000a730b000) (0MB)
[    0.000000] EFI: mem31: type=0, attr=0xf, range=[0x00000000a730b000-0x00000000a731b000) (0MB)
[    0.000000] EFI: mem32: type=10, attr=0xf, range=[0x00000000a731b000-0x00000000a7354000) (0MB)
[    0.000000] EFI: mem33: type=10, attr=0xf, range=[0x00000000a7354000-0x00000000a739b000) (0MB)
[    0.000000] EFI: mem34: type=9, attr=0xf, range=[0x00000000a739b000-0x00000000a73e1000) (0MB)
[    0.000000] EFI: mem35: type=9, attr=0xf, range=[0x00000000a73e1000-0x00000000a73fb000) (0MB)
[    0.000000] EFI: mem36: type=4, attr=0xf, range=[0x00000000a73fb000-0x00000000a7e00000) (10MB)
[    0.000000] EFI: mem37: type=7, attr=0xf, range=[0x0000000100000000-0x000000023f000000) (5104MB)
[    0.000000] EFI: mem38: type=11, attr=0x8000000000000001, range=[0x00000000fed80000-0x00000000fed81000) (0MB)
[    0.000000] ACPI: UEFI 00000000a73e7000 0003E (v01 FUJ    PC       00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000a73e6000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000a73e1000 0012A (v01 FUJ    PC       00000001 PTL  00000001)
[    5.633936] fb0: EFI VGA frame buffer device
[    6.382641] EFI Variables Facility v0.08 2004-May-17
[    7.739505] fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver
ubuntu@ubuntu:~$ 

```

---

### Post by oldfred on 2011-09-30
If you are in UEFI mode, it will not boot to MBR and will not even see grub legacy's install to the MBR which is just there for protection of the gpt partitioning system.
You then need to reinstall grub's efi modules. I think that was posted earier as I do not know details.

---

