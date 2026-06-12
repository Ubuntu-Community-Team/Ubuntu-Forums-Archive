---
title: "Can't run bios or install windows anymore"
date: 2015-08-30
forum: Installation &amp; Upgrades
---

### Post by tarjouskirjeet on 2015-08-30
I have been using Ubuntu for years (still kind a noob though). And I decided to install Ubuntu on my laptop Samsung NP700Z5C-S02SE , which I later found to be incompatible with linux ([http://ubuntuforums.org/showthread.php?t=2110594](http://ubuntuforums.org/showthread.php?t=2110594)). However somehow I managed to install Ubuntu 12.04 (now running trusty) and make it boot. How it happened, I have no clue...  I guess Ubuntu installation created a boot partition which is  automatically mounted since it seems that there is literally no bootloader on my laptop at the moment.  Now I have come to a point when I would need to install windows 7 back on my laptop and that is just not possible, since I can't change the boot device or anything since the bios is not loading anymore either.  I hope someone could help me out on this. I know it is hard because of my limited knowledge on terminology etc. but I am willing to give more information if needed.  Here is my boot-info summary [http://paste.ubuntu.com/12229670/](http://paste.ubuntu.com/12229670/)

---

### Post by ajgreeny on 2015-08-30
Not sure I can help with your BIOS problem (in fact it's a UEFI problem) but if you need Windows for something urgently you could think about running it in a VM in, for example, Virtualbox.

What specifically do you need to run using Windows, and what spec is your laptop?

I do note in your pastebin link to the boot report that you have a huge number kernels on your Ubuntu system (31, I think) many of which would be best removed, though I do not think they are having any effect on this particular problem of yours.

To clean them up run command ```
sudo apt-get autoremove
``` and you should be left with just the two most recent.

---

### Post by grahammechanical on 2015-08-30
No boot loader = no loading of any operating system.

Does the machine load Ubuntu? If the answer is, Yes, then there is a boot loader. If Ubuntu is the only OS installed then we will not see a boot loader (Grub) menu. The boot loader will simply load Ubuntu. Press Shift at the beginning of the process to pull up the Grub boot menu.

I do not know why Boot Repair is reporting that there is no boot loader installed in the MBR. I suspect it is because the machine has a UEFI boot system and not a BIOS boot system. But I do not know for sure.

Load into Ubuntu and run this command

```
sudo update-grub
```

If that command produces a screen print listing all the Linux kernels on that machine, then you have confirmed that you really do have a Grub boot loader. And you have a list of all the kernels. Then use Synaptic Package Manager to remove all the kernels but the newest two kernels.

I cannot help with the problem you are having accessing the UEFI boot system. A user guide for that machine might give some useful information.

You will need to create space on that hard disk for Windows. Use a Ubuntu live session and Gparted to resize the Ubuntu partitions. Then use the Windows installer disk to create and format the unallocated space into Windows partitions, then the Windows installer will let you install Windows into that partition. But keep in mind that the Windows installer will over-write the Linux boot loader and if you are not careful it will over-write Ubuntu.

Boot Repair can reinstall the Ubuntu boot loader but it cannot fix things if the Ubuntu partitions have been over-written or deleted by Windows.

Regards.

---

### Post by oldfred on 2015-08-30
Your Samsung was one of the models that had the issue. 
Did you update UEFI/BIOS to latest version from Samsumg? 

There were fixes added to Linux to help resolve the issue, but it was not just a Linux issue (Windows could also create issue) but the design of the UEFI. If too many entries in UEFI or its NVRAM UEFI memory became over one half full it would crash. It should house clean its own NVRAM but was not.

You are booting in UEFI mode.
Post this:
sudo efibootmgr -v

Since you have an encrypted /home, you must have regular good backups as with encryption it may be impossible to recover data if system gets corrupted. And if thinking of installing another system a full refresh of backups are required before doing any new install.

Windows 7 defaults to BIOS/MBR installs and will erase drive if you force it to install. You can convert Windows 7 to UEFI installer and create the partitions it needs.
        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[URL="http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI"]http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI

      [/URL]
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[URL="http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html"]http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html

[/URL]
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

[URL="http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html"]
[/URL]

    [URL="http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI"]
[/URL]

---

### Post by tarjouskirjeet on 2015-08-30
Thanks for the advices. In fact I haven't even noticed the cumulated  kernel versions, for some reason autoremove does not remove them  automatically...
The reason I need win7 is that my GF needs a laptop  for school work but she is not that tech savvy. And I already have win7  running on VM, but to be honest it is not smooth enough for primary use  (also there is things that does not work properly on VM).

the update-grub lists the kernel versions so yes I have grub installed. However pressing shift does not bring me any grub option screen.

I installed the latest patch for UEFI/BIOS from Samsung before I installed Ubuntu (2 years ago) and they stated that the version had the needed correction for the bricking problem.

When I run sudo efibootmgr -v then I get nothing listed.

I also have already the UEFI USB stick but it won't run on this laptop (works on my desktop). I can do it again though following these instructions kindly provided by oldfred.

I do disk image backups occasionally to prevent data loss.

---

### Post by oldfred on 2015-08-30
With UEFI it is the escape key, you may have to press several times, to get into grub menu. Only with BIOS was it the shift key.

I have not seen the efibootmgr list not work, unless booted in BIOS mode?
But that may be related to your system?

I normally use synaptic to remove older kernels. I like to keep 2, may let it build to 2 or 4 and then houseclean back to 2.
       Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image

 sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

If you have older kernels from before an upgrade those kernels will not be in the upgrade's list and you have to manually delete all the files related manually. And you may just end up with them in root's trash and have to empty that. Which can be a hassle.

---

