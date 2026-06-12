---
title: "Correct way to install Ubuntu 12.10 with dual Win 8?"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2012-11-22
So, I've read hundreds of post and pages and pages of websites on all the issues surrounding the installation of the dual boot with Win 8 and ubuntu 12.10.

What is the correct procedure and or path to take in completing this task?

Secure boot              Disable to not?  GRUB2 is not affected?
UEFI/GPT    
Partitions                    all primary in UEFI? 
Legacy mode             go to UEFI?
What type of partition ext4 or ext3
Dual boot and hibernation mode, losing information and or not really shutting down windows.
Boot-repair
GRUB2



1. Shrink windows partition with windows disk management, to allow room for ubuntu.  Reboot windows several times.

2. Download Ubuntu 12.10  64 bit version and create start up media  (either CD, USB etc...)

3. Boot from media  ie USB or CD and choose try ubuntu without installing

4. Use Gparted to create two partitions   one for mount /  and the other for swap
     a.    The one for mount is the ubuntu partition.   Primary, EXT4
     b.    the swap is for the swap and choose that as an option   primary, ext4

5. Now choose install ubuntu

6. choose the something else option instead of along side windows or the other options.

7.  On the next screen choose the partition to install ubuntu, the one from step 4a above.

8. You should see the screen and your in ubuntu.


Not sure what to do about secure boot, or some of the other issues.  Anyone want to elaborate on the steps above and or change them.  I think we need to get some directions and work off of that, instead of searching all the websites and wiki's etc....


Thanks,

Dennis

---

### Post by claven123 on 2012-11-22
I've noticed that there are a few post on this forum related to this and it would be nice if anyone who has experience in this process to add to or adjust the directions, so that we could start with something that is workable.

Thanks,

---

### Post by oldfred on 2012-11-23
I have not done it myself, but tried to help and got results from many users. Some highlights.

Windows only boots from gpt partitioning with UEFI. Ubuntu will boot from gpt partitioning with UEFI or BIOS. I use gpt with BIOS, but need a bios_grub partition. With UEFI the first (or maybe second with some Windows installs) must be the efi partition. 

UEFI while a standard is implemented differently by each vendor. 

All partitions with gpt are in effect primary as there are no extended nor logical partitions.

Only the 64 bit version of Ubuntu works with UEFI. Both Windows & Ubuntu have to be booted from the UEFI menu in UEFI mode to install in UEFI mode. Booting in BIOS mode will cause issues. Both Windows & Ubuntu have to be either BIOS or UEFI. But Boot repair can fix BIOS installs by converting from grub-pc (BIOS) to grub-efi (UEFI).

Some have reported being able to boot both Ubuntu & Windows 8 with secure boot on or off after installing Ubuntu. Again may depend on your UEFI.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

 [https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Ubuntu's default is ext4 and has been for many versions. 

 [https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

Grub2 has with 12.10 the newest grub2 version 2.00 which includes compatibility with secure boot. No other version does. 12.04 will get the grub2 2.00 version with the next point release in Jan.
Grub still has a bug in creating a chain load entry to Windows. It creates a BIOS version which does not work. Boot_Repair can fix that also.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

       Dual-boot Windows 8 and Ubuntu 12.10 on UEFI hardware
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)

Windows 7 installs with UEFI that worked.
       UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)

---

### Post by Andrew_nuts on 2012-12-04
Installing Ubuntu along with Windows 8 is almost same as installing Ubuntu with other Windows OS. Only things differ is the GUI rest technical aspect is almost same.

I recommend  
[Steps to Install Ubuntu 12.10 with screen shots]("http://www.fosspedia.com/how-to-install-ubuntu-12-10-alongside-windows/").  :)

---

### Post by claven123 on 2012-12-04
Ok, so how do I roll back to what you suggest.  

BTW, this is pretty much what I and many others have done.

How do you handle the Grub2 and Win 8 issues and the directly booting to windows?

D

---

### Post by oldfred on 2012-12-05
I thought you went with EasyBCD which does not work with UEFI.

[http://ubuntuforums.org/showthread.php?t=2086383&page=4](http://ubuntuforums.org/showthread.php?t=2086383&page=4)

Where are you at, you never posted the BootInfo report from Boot-Repair. 

And you should use Boot-Repair to resolve the bug in grub2's os-prober not creating the correct chain load entries.
       Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

    
If you are booting Windows and have Ubuntu correctly installed, you do have to go into the UEFI menu and choose to boot ubuntu.

---

### Post by ClaytonP9 on 2013-04-02
[FONT=Liberation Serif]*I changed secure boot to off [/FONT] 
 

 [FONT=Liberation Serif]1) Shrink the windows partition using windows disk management.[/FONT]
 [FONT=Liberation Serif]    * allows room for Ubuntu[/FONT]
 [FONT=Liberation Serif]**    * Reboot several times**[/FONT]
 
 [FONT=Liberation Serif]2) Boot from live CD of Ubuntu 12.10[/FONT]
 [FONT=Liberation Serif]    * Choose try without installing[/FONT]
  

 [FONT=Liberation Serif]3) Use Gparted to make 2 partitions and an empty space following the partitions[/FONT]
 [FONT=Liberation Serif]    *the first partition is the main partition where you will allocate most of the memory[/FONT]
 [FONT=Liberation Serif]        *choose ext4[/FONT]
 [FONT=Liberation Serif]    *the second partition is the Linux swap drive [/FONT] 
 [FONT=Liberation Serif]        *make sure it says swap-drive[/FONT]
 [FONT=Liberation Serif]        *I am using a computer with a Tera-bite hard-drive so I put 9 GB in it [/FONT] 
 [FONT=Liberation Serif]            *I would like to know what the minimum is.[/FONT]
 [FONT=Liberation Serif]    *finally leave 100 MB as free/unallocated space at the end of the partition[/FONT]
 [FONT=Liberation Serif]        *it becomes the boot Grub[/FONT]
 [FONT=Liberation Serif]        *must be at the end? Had problems when at the beginning but it may have been a             different issue[/FONT]
 [FONT=Liberation Serif]    *exit Gparted[/FONT]
 [FONT=Liberation Serif]***do not mess with unknown space it is part of win 8**[/FONT]
 

 [FONT=Liberation Serif]4) Click on “Install Ubuntu”[/FONT]
 [FONT=Liberation Serif]    *choose language[/FONT]
 [FONT=Liberation Serif]    *if you want to read release notes do it now[/FONT]
 [FONT=Liberation Serif]    *click continue[/FONT]
 

 [FONT=Liberation Serif]* I always install third party software but I update after installed[/FONT]
 [FONT=Liberation Serif]    *can take a long time to update[/FONT]
 [FONT=Liberation Serif]    *click continue[/FONT]
 

 [FONT=Liberation Serif]5) Installation Type[/FONT]
 [FONT=Liberation Serif]    *choose “do something else”[/FONT]
 [FONT=Liberation Serif]        *continue[/FONT]
 

 [FONT=Liberation Serif]6) locate the first/biggest drive you made in Gparted (the one you want to put Ubuntu on)[/FONT]
 [FONT=Liberation Serif]    *double click it to edit partition[/FONT]
 [FONT=Liberation Serif]        *change “use as” to “ext4 journaling file system”[/FONT]
 [FONT=Liberation Serif]        *click format drive[/FONT]
 [FONT=Liberation Serif]        *select mount point[/FONT]
 [FONT=Liberation Serif]            *i used “ / ”[/FONT]
 [FONT=Liberation Serif]    *exit the partition[/FONT]
 

 [FONT=Liberation Serif]7) Locate the second drive (the one you made a swap-drive)[/FONT]
 [FONT=Liberation Serif]    *double click to edit partition [/FONT] 
 [FONT=Liberation Serif]        *make sure it says swap area or swap-drive or swap...[/FONT]
 [FONT=Liberation Serif]    *exit partition[/FONT]
 

 

 

 [FONT=Liberation Serif]8) Locate the 100 MB of unallocated space (the 100MB you saved in step 3)[/FONT]
 [FONT=Liberation Serif]    *double click to edit space[/FONT]
 [FONT=Liberation Serif]        *change the “use as” to “reserved bios boot area”[/FONT]
 [FONT=Liberation Serif]        * do not change any other settings[/FONT]
 [FONT=Liberation Serif]    *exit partition[/FONT]
 [FONT=Liberation Serif]    *wait a minute for the computer[/FONT]
 

 [FONT=Liberation Serif]***Only use spaces that you made in Gparted **[/FONT] 
 [FONT=Liberation Serif]***do not change any settings in the drop-down menu at the bottom of the screen**[/FONT]
 

 [FONT=Liberation Serif]**9)Click Install** [/FONT] 
 [FONT=Liberation Serif]    *hope for the best[/FONT]
 [FONT=Liberation Serif]    * I was trying to install the nvidia drivers but kept bricking ubuntu so I ran this process several     times[/FONT]
 

 

 [FONT=Liberation Serif]    This process worked on my Dell Insperon 7720.  I still have to go through the bios and switch between legacy boot for Ubuntu and uefi for win 8, so this is a ugly work around.  I'm still hoping for something better.[/FONT]
 

 [FONT=Liberation Serif]All tab space gets left out of the post?[/FONT]
 

 [FONT=Liberation Serif]Special thanks to Denis who made it possible for me to dual boot my computer and the first part of my instructions.[/FONT]
 

 [FONT=Liberation Serif]Thanks,[/FONT]
 

 [FONT=Liberation Serif]Clayton[/FONT]

---

### Post by oldfred on 2013-04-02
If you boot Ubuntu installer  in UEFI mode (not all systems let you), it will install in UEFI mode and let you dual boot from grub menu. You still need fixes from Boot-Repair for correct chain load entry.

Since you installed in BIOS mode you do have to go into UEFI change to BIOS or vice versa. But you can use Boot-Repair to convert your BIOS/CSM mode install to UEFI. It uninstalls grub-pc(BIOS) and installs grub-efi(UEFI) and modifies a few settings. Then you can dual boot from the grub menu.

Some systems work with secure boot on. Some only work with secure boot off. And some only boot Windows efi file, but Boot-Repair has a work around, renaming files.

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

   Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.


 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

