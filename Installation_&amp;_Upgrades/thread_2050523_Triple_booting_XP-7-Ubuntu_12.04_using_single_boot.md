---
title: "Triple booting XP-7-Ubuntu 12.04 using single boot screen"
date: 2012-08-31
forum: Installation &amp; Upgrades
---

### Post by sangeethar44 on 2012-08-31
Hi,
I found many articles/guides on triple booting Win 7, Win XP and Ubuntu 12.04with a single boot menu and i just could not get it working on my system. I could only get grub2 menu with Ubuntu and Win 7 boot loader, with Win 7 bootloader again giving an option of entering either Win7 system or Win XP, but not all the three OS's on a single menu. 
I have the following partitions on my 1TB single HDD:
 
**C: Win XP** - *Primary*, 80 GB
**D: Win 7** - *Primary*, 80 GB
**E: Ubuntu 12.04**, *Primary*, 25 GB
F: NTFS data partition, Logical, 350GB
G: NTFS data partition, Logical, 350 GB
 
I tried installing XP first, then taking off boot flag on C drive using gparted, then installing Win 7, then again taking off boot flag on drive D using gparted and finally installing Ubuntu. I tried trial and error methods and i just could not get it to work and i gave up. Any help is greatly appreciated. Also i would prefer using GRUB2 menu, since i plan to install BURG bootloader. Thanks in Advance.

---

### Post by darkod on 2012-08-31
Don't take the boot flag off the second time, some systems need it to exist on one partition. Linux doesn't use it, so you can leave it on one of the windows partitions.

You seem to be doing it right. I would prepare the hdd in Gparted using ubuntu live mode first. Make the both ntfs partitions and set the boot flag on #1.
Install XP on #1.
Boot ubuntu live mode again and turn off the boot flag on #1, turn it on on #2.
Install win7 on #2.
Leave the flag on #2, doesn't matter. Install ubuntu.

That should be it.

---

### Post by sangeethar44 on 2012-08-31
> **darkod said:**
> Don't take the boot flag off the second time, some systems need it to exist on one partition. Linux doesn't use it, so you can leave it on one of the windows partitions.
 
You seem to be doing it right. I would prepare the hdd in Gparted using ubuntu live mode first. Make the both ntfs partitions and set the boot flag on #1.
Install XP on #1.
Boot ubuntu live mode again and turn off the boot flag on #1, turn it on on #2.
Install win7 on #2.
Leave the flag on #2, doesn't matter. Install ubuntu.
 
That should be it.
 
Thanks darkod! I will try this during the weekend and update you. So, this will give me single grub2 boot screen right? Also, would installing BURG bootloader after ubuntu also give me all the three OS on a single boot screen?

---

### Post by darkod on 2012-08-31
Yes, moving the boot flag before the win7 install (the second windows install) is done so that the boot files of the two windows installations are separated. Otherwise, windows combines them, which has nothing to do with grub. If they are combines, grub shows one entry in the menu because it can't show otherwise.

If the boot files are separate, it will show two windows entries in the menu.

I have no idea how BURG works.

---

### Post by oldfred on 2012-08-31
+1 on Darko's suggestions.

You may be able to move boot flag and run repairs as Windows always litterally moved its boot files from a second install to the first. You may have to repair XP also as its PBR partition boot sector was converted to Windows 7 style.

Some related info:

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You may be able to just move boot files back to correct install then run repairs for each.

If you want to see details of what is installed where or just document install. Run BootInfo
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

You may need repairCD/USB.
Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by sangeethar44 on 2012-09-05
Guys, Thanks alot. There were no issues in the installation. I followed the instructions as told and it worked like charm. The only mistake i used to do before was that before installing Windows 7, i used to remove the boot flag from Windows XP drive, but would not flag the Windows 7 drive.
 
Will check if the burg manager works with triple booting using a single boot menu and update.

---

### Post by bhishmar on 2012-11-10
Hi sangeethar44
It would good if you could giveback some help to others, after taking help from these forums.
In that spirit can I have a clarification from you?
Can u please elaborate on the steps you did to make it work?
Specifically:
> **sangeethar44 said:**
> .....
 There were no issues in the installation. I followed the instructions as told and it worked like charm. 
.....
What instructions?
Instructions of darkod?   OR
Instructions of oldfred?  OR
Instructions of BOTH?

thnks & rgds

---

### Post by oldfred on 2012-11-10
The instructions from Darko & me were not different.

I just added some links with others who also had it work and explained how they did it and some links to details on how Windows multi-boots.

---

