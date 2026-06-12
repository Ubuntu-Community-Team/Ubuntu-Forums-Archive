---
title: "Triple Boot Windows 8, Windows XP and Ubuntu"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by spnoe on 2012-11-21
I am trying to install three operating systems on two Hard Drives. I have installed Windows 8 64bit to one HD and Windows XP and Ubuntu to another.

The problem I have is that Windows 8 takes over the Grub. I installed Windows 8 first on the separate HD, thinking that I could boot this on its own. I then partitioned the other HD and installed Windows XP and then Ubuntu.

On booting the system Windows 8 did not show up on the Linux boot screen. All well and good. When I tried to boot Windows 8, I got a Grub error. So I reinstalled Windows 8 and run a Grub Repair disk and now Windows 8 starts from the Linux Grub list but the List still says Windows XP. So now I can not boot XP.

Could someone advise me how to redirect the Grub to show and boot the Windows OS's and Ubuntu.

The only reason I need the two Windows operating systems is that I have a few programs that will only run on these systems.

I would very much appreciate any help.

Thank you, Steve

---

### Post by oldfred on 2012-11-21
Windows only boots from one active partition (boot flag) on one drive. So all the boot files are really on the one active partition on the drive that BIOS boots from. Best to install separately, but you may be able to repair installs.

       Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
Older so not sure of any changes with Windows 8, but should be similar to Windows 7 and Vista.
       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by spnoe on 2012-11-23
Thank you very much for your prompt and helpful reply. I have managed, with your help to repair or change the boot Grub. It is now working. Thank you very much.
Steve

> **oldfred said:**
> Windows only boots from one active partition (boot flag) on one drive. So all the boot files are really on the one active partition on the drive that BIOS boots from. Best to install separately, but you may be able to repair installs.

       Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
Older so not sure of any changes with Windows 8, but should be similar to Windows 7 and Vista.
       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by Desprit on 2013-02-02
I am searching information I lost. I have memory problems regarding names of things so I take prodigous notes. Digital, not paper which can get as corrupted as my memory. I hope I can make my question clear with incorrect or missing names of things. Thanks to those who bear with me and espesially anyone who can help.  I have a similar problem to spnoe and the solution I wost would fix the dual drive problem too. I was triple booting Vista, Win7, and Fedora across 2 drives. I switched to Ubuntu and my backup software failed to reinstall. I hope someone can help me remember how I did it. I prefer command line since the software options have restricted abilities, limit creativity, and have incompatibilities.  Someone had posted a command that retrieves partition (IDs?) for changing the 40_custom file in grub to allow customization and still permit updates. I used th partition information to link to the Linux partition instead of the kernal (if I'm saying it right) so when the kernal was updated 40_custom stayed current. I used the same drive information to link directly into the Vista OS and left Win7 booting into both but set the wait to '0' with Win7 as default.  If anyone can help me remember the commands or direct me back to the article on customizing grub2 and still allowing updates if it's still online I want to thank you a million times.

---

### Post by oldfred on 2013-02-02
@Desprit
Probably better to start you own thread. But is this what you are looking for. I have used Ranch hand's instructions to boot partitions, cavsfan documented them. Do not know if that works for other than Debian based installs as they put a link to the most current kernel in root.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

    
       Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
    
       The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

