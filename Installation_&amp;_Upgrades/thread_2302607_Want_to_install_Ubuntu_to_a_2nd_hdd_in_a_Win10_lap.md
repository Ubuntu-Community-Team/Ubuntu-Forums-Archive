---
title: "Want to install Ubuntu to a 2nd hdd in a Win10 laptop"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by Mellatau on 2015-11-11
Hello. (Sorry if my english is hard to read)
The laptop is not mine (and I'm sick tired of being unable to do anything without admin's rights), so I placed my half-filled archive HDD (NTFS) in whith an intention to ... (topic name).
(BTW, I'm completely new to Linux, if anything...)

What I'm now thinking of doing:
 - to make a new partition on the disk. Will 64GB be enough (Ubuntu + up to 10 not too big apps)?
 - to install the Ubuntu there from a USB flash.

Is there anything else I should know?


Laptop: Dell Inspiron 17r 7720 (Intel HD4000 + nVidia GT 650M); Win 10 upgraded from Win 8.1.


Thanks in advance)

---

### Post by oldfred on 2015-11-11
If originally Windows 8 then system is UEFI.
Be sure to fully backup Windows before doing anything. And make a Windows repair disk.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

Many more details & links in my signature below.

---

### Post by grahammechanical on 2015-11-11
Ubuntu needs 2 partitions. One for Ubuntu and 64GB should be more than enough. And one for swap which should be a little more than the amount of RAM in case you hibernate the laptop.

That machine has hybrid graphics. If you tick the box "Install third party software" you will get a Nvidia video driver and some free but proprietary audio and visual codecs. Do not expect to the OS to automatically switch between the Intel and Nvidia graphic adapters. Nvidia has not provided a Linux driver to do that. You can make the switch by opening the Nvidia Xserver Settings utility that is installed at the same time as the Nvidia driver. Search for it in the Dash.

You might want to use Windows utilities to create 64 GB of unallocated space on the drive. Then the Ubuntu installer's Install alongside option might off to install Ubuntu into the unallocated space and create the 2 Ubuntu partitions for you.

Is the original hard disk going to be left in the laptop? That might complicate things a little bit.

Regards.

---

### Post by ubfan1 on 2015-11-11
The machine is UEFI if it came with Windows 8.1 preinstalled, so I'd advise putting an EFI partition on the external HDD too.  It's small, 200M-300M, flagged bootable, with a FAT32 filesystem.  You should be able to set up the external disk with the grub bootloader, and not have anything on the internal hard disk, but there's a bug in the installer which puts grub onto the internal hard disk's EFI partition in /EFI/ubuntu.  You can just copy that directory and contents onto the equivalent /EFI/ubuntu on your external HDD's EFI partition (and delete it from the internal hard disk).  Also, for the external media default boot (so no nvram entry is needed to boot it), copy /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi and copy /EFI/ubuntu/grubx64.efi to /EFI/Boot/grubx64.efi.  That will boot with or without secure boot.  Since it's not your machine, be cautious about running boot-repair -- that tends to rename the bootloaders, and install grub everywhere.

---

### Post by Mellatau on 2015-11-12
Thank you all for your replies, but there's some new info about the laptop:
 - it was bought with Windows SEVEN installed, later the HDD was changed and Win8.1 was installed from a DVD (or USB) and then upgraded to Win10;
 - I've managed to move my tiny archive to the first HDD (so I can do whatever with it now), but there's no way in hell I can backup that 1TB thing (I have 1 16GB USB key though, lol);
 - will be able to make some photos of BIOS later, if needed.

Anything new/different with this? And what software should I have in order to be able to do things necessary? Aside from Linux Reader.

---

### Post by oldfred on 2015-11-12
If it is a BIOS based install, then you can install BIOS boot on external drive. Just make sure you change boot loader - grub to install to external drive. Otherwise you will not be able to boot laptop without external drive.  You have to use the somewhat more advanced Something Else where you select and create / (root) and swap partitions. On that same screen is location of boot loader.

Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]
[/URL]

---

### Post by Mellatau on 2015-11-14
Thank you so much for your help! Everything (Win10 included) works just fine. Kubuntu 15.10 didn't even let me bother with graphics and wireless drivers I thought I'd get a lot of problems with, I just had to click "yes" a few times. And the only "hard" thing there was to manually manage the partitioning, which appeared to be really easy with one of the links above.
The only thing that's left is to make that awesome and awful at the same time KDE thing work a bit better than it does now...but I guess it's a topic for another thread?

---

### Post by Bucky Ball on 2015-11-14
> **Mellatau said:**
> 
The only thing that's left is to make that awesome and awful at the same time KDE thing work a bit better than it does now...but I guess it's a topic for another thread?

Correct. :) You might want to try in Desktop Environments for tweaking the look and function of KDE. Please mark this one as solved (see link in my signature). This won't close the thread to further discussion. Good news and good luck. :)

---

