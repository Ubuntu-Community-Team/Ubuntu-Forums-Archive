---
title: "Windows won't boot !"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by PinkPanda on 2012-07-12
I installed Ubuntu 12.04 from a bootable USB stick on a computer that also has windows 7 x64. During the installation I was asked to partition my harddrive which I did. My intention was to have 70 GB for windows and the rest for Ubuntu (125GB SSD harddrive).

After the installation (which went fine and Ubuntu is working perfectly well) I can no longer use Windows 7. When I restart my computer I get something that looks something like this:


GNU GRUB version 1.99-21ubuntu3.1

Ubuntu, with Linux 3.2.0-26-generic
Ubuntu, with Linux 3.2.0-26-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 11520)
Windows 7 (loader) (on /dev/sda3)
Windows Recovery Environment (loader)


When I choose the second to last option (Windows 7 (loader) (on /dev/sda3)) I get the following message: 

error: invalid EFI file path

Press any key to continue...


Is this something that is fixable without having to reinstall windows all over again? I don't have a recovery DVD and I couldn't run the Windows Recovery Environment either, but I have a backup saved on an external harddrive. Anyway that would be my very last option and I'm not even sure how I would do that.

---

### Post by drs305 on 2012-07-12
PinkPanda,

Welcome to the Ubuntu Forums.  :-)

Please click the Boot Repair link in my signature line and try the "Recommended Repair" once you have installed the app. BR is a great app that can solve a wide variety of boot issues.

If that doesn't work, run the boot info script from Boot Repair and post the link to the report. 

Aside: I don't know this from experience but on these forums it's generally recommended to partition the drive from within Windows when that OS is present on the drive. It's not required, it sometimes just eliminates certain problems.

---

### Post by PinkPanda on 2012-07-12
Thanks for the quick reply!

I tried to do the repair but I still have the same problem.

This is the script:

[http://paste.ubuntu.com/1089005/](http://paste.ubuntu.com/1089005/)


I should also mention that when I did the repair it also asked me (and I should have written this down in detail)

*SOMETHING* BIOS boot on sd1/EFI/ubuntu/grubx64.efi file!

---

### Post by VH-BIL on 2012-07-12
Did you partition your drive that already Windows on it?

If you did you may need to reinstall Windows. After installing Windows you will need to put the grub boot loader back on.

---

### Post by PinkPanda on 2012-07-12
Yes I did but I got the impression from reading the installation guides that it this was no problem for the ubuntu installer (but a backup was recommended anyway)

---

### Post by drs305 on 2012-07-12
Edit: Since this is an EFI system I'll defer to someone who uses it.

---

### Post by PinkPanda on 2012-07-12
Alright, cheers

---

### Post by drs305 on 2012-07-12
In this thread Boot Repair and EFI are discussed:
[http://ubuntuforums.org/showthread.php?t=2003442]("http://ubuntuforums.org/showthread.php?t=2003442")

I thought Post #17 might be of use to you. Especially the part of the post that begins 
> **- If you don't know which method you need (grub-pc or grub-efi)**

If the Boot Repair recommended option didn't work, perhaps this explains why.

---

### Post by oldfred on 2012-07-13
The grub entry is a typical BIOS type entry where it bypasses the MBR. But with UEFI I am not sure that works the same.

You are missing the Windows boot files in the efi partition. There was a bug which I thought they fixed where grub overwrites the Windows/Microsoft efi files.

find /boot/efi -name "*efi"
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi

Not sure how to repair or if Windows repairs will restore those boot files in the efi partition. I would try Windows repairs to see it that works.

If efi partition has the correct files these are entries that others have posted on chainloading Windows from grub2. You would have to add one of these to 40_custom.

Chainload entry - adjusted partition & UUIDs to yours:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt2)'
  search --fs-uuid --no-floppy --set=root 4f84-ee2e
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

[http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)
menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

---

### Post by PinkPanda on 2012-07-13
I used the simplest option and reinstalled windows. However the partition that was created during the Ubuntu install is still there for some reason (even though windows was supposed to delete all partitions from the hard disk drive).

So now I have a partition of GB and one (roughly) 75 GB and one of 20 GB. Before the install I had over 100 GB so almost 10 GB is missing.

Since I want to give this another try, is there anyway to make sure the old Ubuntu OS is completly removed? I had to remove it from the boot priority order even though nothing happened when it was chosen (error and restart), And should I be safe from the same problem now that there is a partition available?

---

### Post by drs305 on 2012-07-13
> **PinkPanda said:**
> Since I want to give this another try, is there anyway to make sure the old Ubuntu OS is completly removed? I had to remove it from the boot priority order even though nothing happened when it was chosen (error and restart), And should I be safe from the same problem now that there is a partition available?

If you select the 'Do something else' and manually select the partitions, just make sure to tick the 'format' box if you are using the same partition you used the first time. Just make sure you haven't selected the Windowd partition for formatting. This should ensure the remnants of your old installation are removed.

---

### Post by YannBuntu on 2012-07-13
Hello PinkPanda, and welcome among us :)

> **PinkPanda said:**
> After the installation (which went fine and Ubuntu is working perfectly well) I can no longer use Windows 7. When I restart my computer I get something that looks something like this:


GNU GRUB version 1.99-21ubuntu3.1

Ubuntu, with Linux 3.2.0-26-generic
Ubuntu, with Linux 3.2.0-26-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 11520)
Windows 7 (loader) (on /dev/sda3)
Windows Recovery Environment (loader)


When I choose the second to last option (Windows 7 (loader) (on /dev/sda3)) I get the following message: 

error: invalid EFI file path

Press any key to continue...

= this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

Workaround: boot Windows from the (EFI) BIOS.

Now that you have reinstalled Windows, Ubuntu should have remained, and you just need to use Boot-Repair, then select your system from the BIOS menu.

---

### Post by PinkPanda on 2012-07-13
I have tried to reinstall Ubuntu now but Ubuntu wont boot (after the installation was complete Ubuntu asked me to restart and there was no choice between starting Ubuntu or Windows, Windows started automatically.

This is how the different partitions look like (I'm looking at the Ubuntu installer choosing partitions etc)

```
/dev/sda
 /dev/sda8 biosgrub 1 MB unknown         */ This was free space before but I used it as "Reserved BIOS boot area" becouse the installer asked me to do so with some partition (larger than 1 MB) */
 /dev/sda1 fat32  209 MB unknown         */ Don't know what this is for */
 /dev/sda2        134 MB unknown         */ Don't know what this is for */
 /dev/sda3 ntfs 79402 MB 41181 MB (used) */ Windows partition */
 free space         0 MB
 /dev/sda4       4293 MB unknown         */ I figure this is a swap kind of thing but for windows */
 free space         0 MB
 /dev/sda5 ext4 20749 MB  3357 MB (used) */ Here I installed Ubuntu (I think... I checked formated and mount point /) */
 /dev/sda6 swap  4175 MB     0 MB (used) */ This was the use as swap area */
 free space      4294 MB                 */ 4 GB of free space seems like a waste, should I use this somewhere? */
 /dev/sda7 ntfs 10737 MB  7569 mB (used) */ Think this is the recovery partition (I'm using an ASUS laptop so no recovery CD) */
 free space         0 MB

```

For "Device for boot loader installation" I selected 

/dev/sda ATA SanDisk SSD U100 (124.0 GB)

Which I think should be correct ...


Hope all this will be understandable... Where did I go wrong?

P.S. Since the subject has changed a bit maybe I should create a different thread?

---

### Post by YannBuntu on 2012-07-13
You can continue here.
Please run Boot-Repair again, and indicate your new Boot-Info URL.
This will give us valuable information to help you.

---

### Post by PinkPanda on 2012-07-13
But I cant use Boot Repair since I can't get into Ubuntu. On startup the computer simply starts Windows without displaying the Ubuntu option.

---

### Post by oldfred on 2012-07-13
You should be able to use the liveCD or USB that you used to install. Just do not select install but try Ubuntu and that is a full system.

---

### Post by YannBuntu on 2012-07-13
You can do it from a live-CD (or live-USB). 
See [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by PinkPanda on 2012-07-13
Okay, I'm doing this right now but it is painfully slow scanning the system, has been going on for about 30 minutes I think. It doesn't appear to be stuck though so I'll leave it on a few minutes more.

---

### Post by PinkPanda on 2012-07-13
I had to cancel the repair becouse it took too long, but after running it again it made me type a few things in the terminal and this was the result:



An error occurred during the repair.

Please use Ubuntu-Secure-Remix-64bits (sourceforge.net/p/ubuntu-secured) which contains an EFI-compatible version of this software.
Please note the following URL: [http://paste.ubuntu.com/1090733/](http://paste.ubuntu.com/1090733/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] 

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file!


I will check what happens when I restart.

EDIT: It is still only booting Windows.

---

### Post by Petro Dawg on 2012-07-13
> **PinkPanda said:**
> I have tried to reinstall Ubuntu now but Ubuntu wont boot (after the installation was complete Ubuntu asked me to restart and there was no choice between starting Ubuntu or Windows, Windows started automatically.



Yeah that sounds normal to me.  Just download EasyBCD (free version) on windows and set up the linux boot from there.  After you get it set up you will get the choice between windows and linux.

This link should show you how to do it.

[http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/2/](http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/2/)

---

### Post by PinkPanda on 2012-07-14
> **Petro Dawg said:**
> Yeah that sounds normal to me.  Just download EasyBCD (free version) on windows and set up the linux boot from there.  After you get it set up you will get the choice between windows and linux.

This link should show you how to do it.

[http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/2/](http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/2/)

I checked that out and noticed this guide recommends installing the boot loader on the /boot partition (I had it on /dev/sda). I tried to reinstall ubuntu doing this following exactly what the guide said (but 4GB on the swap)

A message appeared when I clicked install:

The patition table format in use on your disks normally requires you to create a separate partition for boot loader cod. This partition should be marked for use as "Reserved BIOS boot area" and should be at least 1 MB. Note that this is not the same as a partition mounted on /boot."

I ignored this and the install crashed, Windows still works fine though.

---

### Post by oldfred on 2012-07-14
It looks like you have UEFI and a gpt partitioned drive. Windows only boots from gpt partitioned drives with UEFI. But it also looks like you have Ubuntu installed in BIOS mode not UEFI.

You have to be careful on most instructions as they are for BIOS/MBR not UEFI/gpt. I also do not think EasyBCD works with UEFI either.

Best to have Ubuntu & Windows both installed in UEFI or if you want to convert back to MBR and totally reinstall in BIOS/MBR. Those that were successful in stalling partitioned in advance. Both Window & Ubuntu should from UEFI menu for installing offer two options - one UEFI/efi and the other BIOS/AHCI/legacy or whatever your UEFI happens to call it. Whichever mode you boot installer/liveCD or USB in is how it will install.

Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.

UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
GUIDE: (U)EFI installation Also full install post *52 superfreak pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

---

### Post by Petro Dawg on 2012-07-14
It took me a while to find, but these the EXACT guides I used to do my dual boot (Win7 and 12.04):

Most of what you need to do will be in this article:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
Follow it to the letter.  The only deviation between what it said to do and what I did was that I left about 1/2 Gig (512MB) unallocated (or free) on my hard drive because the first time I tried  using %100 of the drive, the windows boot loader became corrupted.  That may have just been a fluke, but I just like to leave a little extra room now just in case.

This is an other article I used and found useful:
[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)

I recommend doing a completely clean install of windows7, then use the partitioning software in windows to shrink the volume to about 50% (or whatever you are comfortable with) of the hard drive.  Then follow the  linuxbsdos.com guide (EXACTLY).

Its a pain to start all over again, but partitioning your hard drive is something that should be done perfectly from the start to keep you from having issues later down the road, its worth the time to do it right.

Also, if your computer has a recovery partition with windows on it, you'll need to create some system restore disks **_AND_** a system repair disk _**BEFORE**_ doing the partition because the recovery partition will probably need to be deleted to be able to create the partition for linux.

---

### Post by PinkPanda on 2012-07-14
> **oldfred said:**
> It looks like you have UEFI and a gpt partitioned drive. Windows only boots from gpt partitioned drives with UEFI. But it also looks like you have Ubuntu installed in BIOS mode not UEFI.

You have to be careful on most instructions as they are for BIOS/MBR not UEFI/gpt. I also do not think EasyBCD works with UEFI either.

Best to have Ubuntu & Windows both installed in UEFI or if you want to convert back to MBR and totally reinstall in BIOS/MBR. Those that were successful in stalling partitioned in advance. Both Window & Ubuntu should from UEFI menu for installing offer two options - one UEFI/efi and the other BIOS/AHCI/legacy or whatever your UEFI happens to call it. Whichever mode you boot installer/liveCD or USB in is how it will install.

Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.

UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
GUIDE: (U)EFI installation Also full install post *52 superfreak pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

I've tried to make sense of all this so I think I realized that the EFI partition is key. So when choosing partitions, should I still have the / and swap as before but select the EFI partition as /boot? Or is this something I should do before I start the installation? What about the warning I recieved about choosing a partition "Reserved for BIOS boot area"?

---

### Post by oldfred on 2012-07-14
The efi partition is not a /boot nor Windows boot partition. For most desktops you do not need a separate /boot. Windows has the separate boot partition so those who want to encrypt the main partition or c: drive can as boot files cannot be encrypted.

The bios_grub partition is when you have gpt partitioning but install in BIOS mode. Grub needs space for some parts of its boot files that normally is in the few sectors just after the MBR in BIOS/MBR. But gpt does not have that space so a small 1MB unformated bios_grub partition is required. You should not need it if booting with UEFI, but it is only 1MB so I ofter create it and the efi partition just to have them in case I use drive in a different system.

The important thing is to boot installer in UEFI mode and when installing grub-efi, it has to be installed to the efi partiton. No other files go into the efi partition. Also back up the Windows files in the efi partition before installing Ubuntu. I thought the bug was fixed but someone just posted they had the problem where Ubuntu overwrote the efi partition. See below for files in efi partition.

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)

When in BIOS mode grub is installed to the MBR of the boot drive or sda typically. gpt drives have an MBR just for protection from old tools that expect one. The MBR can be used to boot in BIOS mode but in UEFI mode is not used for booting.

Someone posted this as the contents of their efi partition for both Ubuntu & Windows:
find /boot/efi -name "*efi"
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi

---

### Post by YannBuntu on 2012-07-14
> **PinkPanda said:**
> Please note the following URL: [http://paste.ubuntu.com/1090733/](http://paste.ubuntu.com/1090733/)

Hello

according to this log, you have nearly everything correctly setup (GPT disk, EFI partition, grub-efi with /efi/ubuntu/grubx64.efi file).

The only problem I see is that **your BIOS is not setup in EFI-mode.**

Please :
1) Enter your BIOS setup to see if there is an Ubuntu entry or not in it. If yes, try to boot on it.

2) If there is no Ubuntu entry, or if the Ubuntu entry fails, please boot your Ubuntu CD in EFI-mode (if you don't know how, please show us pictures of your BIOS), then use Boot-Repair again.

---

### Post by PinkPanda on 2012-07-14
It works!

I installed it by choosing the UEFI option when choosing how to boot the USB stick. After the installation was finished I couldn't start windows just like before. This time I went and edited the 40_custom file that oldfred already mentioned a while ago but I gave up too quickly then :P. I chose the last option, is there any difference between them? Then I made the file executable and a new option appeared when starting the computer. The old ones still don't work but there is now a new option, Windows 7 UEFI which works fine.

I appreciate all the help, thank you very much! :D

---

### Post by PinkPanda on 2012-07-14
Btw, it possible to reduce the number of options that you get when starting the computer or at least have the Windows option first so that it starts automatically if no choice has been made after a few seconds?

---

