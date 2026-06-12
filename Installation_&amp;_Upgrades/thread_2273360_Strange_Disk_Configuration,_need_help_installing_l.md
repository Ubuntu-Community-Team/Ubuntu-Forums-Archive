---
title: "Strange Disk Configuration, need help installing linux"
date: 2015-04-12
forum: Installation &amp; Upgrades
---

### Post by ajthemacboy on 2015-04-12
Hi! Let me start by saying that I've read lots and lots of guides. This is a pretty common question, but no other forums seem to have an answer for my old, bad, strange disk configuration. I've had so many OS installs on this laptop that everything is pretty messed up.

That said, I'm running Windows 8.1 on a NTFS formatted partition, and I want to install Linux alongside it on another partition I've already made.

I hope that someone can just look at the information and provide and tell me what to do. Here's a screenshot of Disk Management in Windows, with my current disk setup: [http://gyazo.com/4ec9bbff6c60405ceb21d4288808026f](http://gyazo.com/4ec9bbff6c60405ceb21d4288808026f)

The partition I want to install on is drive D. This currently has Windows 10 Technical Preview installed. I want to use Ubuntu in the long run. 

Here's a screenshot of the two Properties windows of drives C and D: [http://gyazo.com/6ad93f0841da3c2859f1669c9956129e](http://gyazo.com/6ad93f0841da3c2859f1669c9956129e)

I can provide any additional information you need. I don't need new instructions, if you can just link me to a guide, that's all I need.

Thanks for your help!

-AJ (ajthe[linux]boy)

---

### Post by grahammechanical on 2015-04-12
You do not actually say what the problem is. Or what it is that is stopping you from trying to install Ubuntu.

The installer gives us choices:

1) Install alongside other operating systems. If you have two hard drives it is best to disconnect the hard drive that you do not want to install Ubuntu on otherwise the installer mat create space on the drive with the most space available by shrinking partitions with lots of unused space.
2) Erase disk and install Ubuntu. Again it is best to disconnect the drive that you do not want erased. You will lose all data and everything on the drive that gets erased.
3) Encrypt the new Ubuntu installation for security
4) Use LVM with the new Ubuntu installation
5) Something Else

It  is my guess that you need to create space for Ubuntu to be installed into. We use Windows utilities to defrag Windows at least twice and make sure that Windows loads each time. Then we use Windows utilities to shrink Windows partitions to create unallocated space on the disc.

Next we load the Ubuntu live session desktop and open the disk partitioner called Gparted and use that to create at least two partition for Ubuntu out of the unallocated space. One partition should be 15 GB to 20 GB in size. That is for Ubuntu. The other partition should be about 2 GB in size (in my opinion) and that is for swap. Then we run the installer and use the Something Else option to tell the install which partition to install Ubuntu in and which partition is to be used as swap.

So, what do you want to do? Have you identified partitions that you no longer need?

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If you have already selected an existing partitions to use for Ubuntu, then you use the Something Else option. If I am repeating what you already know it is because you have not told us what it is that you do not know.

Regards.

---

### Post by yancek on 2015-04-12
In addition to what is posted above, you will not see any "D" partition when you install Ubuntu.  Linux naming conventions are different.  Also, since you have windows 10 currently installed the filesystem is ntfs so you will have to change that and format the partition with a Linux filesystem (probably ext4) during the install.  A tutorial at the link below:

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by ajthemacboy on 2015-04-13
Ok, I didn't mention my problem. Every time I install Ubuntu (or any Linux distribution) on a partition I've already made (I want to install on the D: drive, which I know won't be called D in the Ubuntu installer), the Windows bootloader gets broken. Each time, I have to either reset the entire disk, or hope that the Windows 8 install disk I have can repair it (it usually can't.)

I've run the disk repair program (I forget what it's called), I've tried booting Puppy Linux to save the files and to use Gparted to fix the errors, I've tried installing Grub, not installing Grub, and a lot more. It never works! I'm not a 'noob' with computers; I'm familiar with how disk partitions work, what a bootloader is, the different types of both, etc. I don't know what I'm doing wrong, and that's what I need help with.

---

### Post by dino99 on 2015-04-13
Some basic comments:
- no more than 4 primary partitions (linux naming of what is called C:, D: in windows world); so to give you freedom, set 1 or 2 primary and 1 extended where you then can set lot of partitions if you wish.
- as i know, windows want to be on the first partition. So delete all your empty ones at the hdd beginning, and move/shrink windows partition (after having made some cleaning (ccleaner) and defrag)
- usually ubuntu is installed with 3 partitions: / (root) about 10/12 gb for the OS (ext4) with a 'boot' flag, a swap of 4 gb, and /home for your data & settings (ext4)
- so you can create them first with gparted for example, then select 'something else' when the ubuntu iso installer will ask for the partitions.
- finally set the grub bootloader to /dev/sda

---

### Post by ubfan1 on 2015-04-13
Is this a UEFI machine?  I can't tell much from your screenshot except there is a small initial partition which might be an EFI partition.

---

### Post by oldfred on 2015-04-13
Almost has to be UEFI.
Too many partitions without either an extended partition or Windows converting from basic to dynamic (which you never ever want). So with all those partitions it has to be gpt partitioned and Windows only boots from gpt with UEFI.

If you install Ubuntu in UEFI mode, can you not boot both systems? But Ubuntu must be in UEFI mode not BIOS/CSM boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    
You need to make sure fast startup or the always on hibernation is off in Windows. And if you have a fast boot setting in UEFI make sure it is off also.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
This should be more similar to Windows 10 & Ubuntu in UEFI mode:
 Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Or:

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by ajthemacboy on 2015-04-14
Ive tried to install in both UEFI and CSM (legacy) mode before. If I remember correctly, UEFI messed up the EFI partition and I had to delete all my data to restore it (this was the conclusion of a long forum thread I had once after another time trying to install Ubuntu.)

Legacy mode made it so I can only boot Ubuntu once, and the other time it just spams errors when it boots, and brings up the GRUB terminal. (I don't remember the exact error but apparently it's a pretty common issue with not any good solutions.)

If you can tell me exactly which guide to follow, I will do it to the letter, but I don't know which one to follow. 

I probably need to do something with my partitions as well before I install, but I don't know what.

---

### Post by oldfred on 2015-04-14
Backup efi partition before you start. And backup Windows & any data partitions you have first.
Make a Windows repair flash drive if you do not have a way to boot Window other than install.
Make sure fast startup is off in Windows and fast boot in UEFI.

Then any one of the UEFI guides using Something Else should work. They all are essentially the same. And they include screenshots so you have a better idea of what is happening.

If then you have issues booting, run Boot-Repair from live installer and post link to its summary report.

---

### Post by ubfan1 on 2015-04-14
Also search the forum and askubuntu.com for any problems with machines just like yours -- they all seem to have individual quirks.

---

### Post by ajthemacboy on 2015-04-16
How do I backup the EFI partition in Windows? And how can I restore it if I mess up?

---

### Post by oldfred on 2015-04-16
I would do it from the Ubuntu live installer. And just copy to a flash drive or another hard drive. Then you can copy back. 
I think in Windows you have to mount as efi is not normally shown, but from Windows if UEFI broken then you could not copy back with Windows.

---

### Post by ajthemacboy on 2015-04-17
Sorry, I finally got some time to try this and I can't figure out how to backup the efi partition. I can't find any information about backing it up. 

I'm on the live desktop of Ubuntu. I just don't know what to do from here.

---

### Post by ubfan1 on 2015-04-17
The UEFI bootloaders are just file sitting in a FAT filesystem.  You mount the (EFI) partition (read only just for safety) (assume sda1 below):
sudo mount -tvfat -oro /dev/sda1 /mnt
Then you just copy everything off what in /mnt  somewhere, like a USB stick.

---

### Post by ajthemacboy on 2015-04-18
Thanks, everything is working now! Your help is greatly appreciated.

---

### Post by ajthemacboy on 2015-04-18
Whoops, spoke to soon.. Now I can't boot into windows. I tried using bootrec to repair the mbr, and to rebuild the bcd. Rebuilding the bcd returns "The requested system device cannot be found."

I think the problem is, it's still thinks windows 10 (now deleted) is the first thing it should boot. How do I change it back to windows 8?

---

### Post by oldfred on 2015-04-18
With MBR, Windows only has one bootable (active) partition. We see that as the boot flag.
All boot files for all installs are in the one partition with the boot flag. Or second install's BCD takes over first install in first install's boot partition.

So do you have a primary NTFS partition with the boot flag and bootmgr & BCD? If not you need to use Windows to repair install.

---

### Post by ajthemacboy on 2015-04-18
Are there any instructions you can give me? I have a windows repair disk, and I did create the recovery flash drive. 

I really don't know about my partitions. I have a ntfs partition, I could boot it before I installed Ubuntu, so I assume it's primary and bootable. I think the bcd was stored on the windows 10 partition, which now houses Ubuntu.

---

### Post by oldfred on 2015-04-18
Need to see details. But you cannot create a BCD from Ubuntu. 
You can use EasyBCD or if in Windows repair console bcdedit.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ajthemacboy on 2015-04-19
Boot info: [http://pastebin.com/DpfgL7jW](http://pastebin.com/DpfgL7jW)

---

### Post by oldfred on 2015-04-19
I cannot tell for sure what your Windows configuration is. How did you install it BIOS or UEFI.
You have Windows UEFI boot files in efi partition, but also have a Windows boot loader in the gpt protective MBR sector for BIOS boot.

And some of your Windows efi files are renamed. 

```
 Boot files:        /EFI/BOOT/BOOTIA32.efi /EFI/BOOT/bkpbootx64.efi
                       /EFI/BOOT/bootx64.efi /EFI/ubuntu/MokManager.efi
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi
                       /EFI/Microsoft/Boot/bkpbootmgfwORIGINAL.efi
                       /EFI/Microsoft/Boot/bootmgfw.efi
                       /EFI/Microsoft/Boot/bootmgfwORIGINAL.efi
                       /EFI/Microsoft/Boot/bootmgr.efi
                       /EFI/Microsoft/Boot/bootx64.efi
                       /EFI/Microsoft/Boot/memtest.efi


```

From UEFI menu you should be able to boot the Windows entry which uses bootmgfw.efi. But if that now is grub you just loop. If you installed in BIOS mode, you have to boot from UEFI menu and turn off UEFI and turn on CSM boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by ajthemacboy on 2015-04-20
I disabled legacy mode (back to UEFI) and couldn't boot. Then I ran boot-repair from my install USB with no luck either. I don't really understand what I need to do to restore the Windows bootloader. Can you give me any noob-friendly instructions?

---

### Post by oldfred on 2015-04-20
It is not an Ubuntu or grub issue.
Still do not know if original Windows was UEFI, but it looks like it was. But if installed in BIOS mode it may not be repairable or becomes a major conversion which I do not know about.

But either way it all is Windows repairs, as grub only really boots a working Windows.
And then you have to run Windows repairs when booted in UEFI mode from a Windows repair or install disk's repair/recovery console.

 Windows 8 UEFI fixes
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
Repair Windows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
Not free but they are good tools
[http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/](http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/)

[http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html](http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html)

[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by ajthemacboy on 2015-04-20
Following answer 2 of this guide fixed my issue: [http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)

Thank you soooo much! Now I just need to use a program like EasyBCD to add Ubuntu back to the entry list, right? Either way I think I can figure it out from here. Thanks a ton!

---

### Post by oldfred on 2015-04-20
I have seen this, but often better to use grub, but you may have to efi folders in efi partition. Links to details in link in my signature if desired.

bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
    [https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)
    UEFI NVRAM boot entries are cached in the BCD store
    BCD has 1:1 mappings for some UEFI global variables
    Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

---

### Post by ajthemacboy on 2015-04-21
I actually reset the entire EFI partition and the only thing in it now is the Windows boot manager. How do I copy GRUB back to it without erasing it?

Also, once I install GRUB, will GRUB autodetect the Windows installation and add it as a boot option? Or does it create 2 boot managers in BIOS?

---

### Post by oldfred on 2015-04-21
You get both.
When you do a grub install, it adds an entry to UEFI  and a folder with all of grub's efi boot files.
The copy of grub in Ubuntu then is updated with os-prober which will find the Windows entry in the efi partition and create a chain load entry to that. For whatever reason direct from UEFI to Windows efi boot files and chain from grub are somewhat different as Windows when hibernated will not work from grub.

If you have a backup of the efi partition with the ubuntu folder you can just copy that back. And the UEFI does not seem to auto erase unless you somehow totally reset.  These are the files you need:
/EFI/ubuntu/MokManager.efi
 /EFI/ubuntu/grubx64.efi 
/EFI/ubuntu/shimx64.efi
/EFI/ubuntu/grub.cfg

The grub.cfg is just a config file entry to the full grub.cfg in the main Ubuntu install.
I have reinstalled a second copy of Ubuntu and had to update grub.cfg with correct UUID & partition.

If you do not have backup, you can use Boot-Repair, but rather than an auto fix, use advanced mode and the full uninstall/reinstall of grub.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

