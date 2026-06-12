---
title: "Aspire V7 482pg - no detected operating system"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by Jesse_Taft on 2014-10-20
I'm trying to install the latest Ubuntu (14.04.1) for dual-boot with Windows 8.1 on my Acer Aspire  V7 482pg-9642. The live OS loads fine from USB and everything seems to work great, but when I try to install it always says "This computer currently has no detected operating systems.” 

I've searched around and looked at a lot of posts about this issue and I've tried every recommendation I could...I've already shrunk my windows partition to make unallocated space for the Ubuntu install, I disabled secure-boot, I disabled Windows fast-startup, tried disabling UEFI and running in legacy mode, I've run chkdsk and found no errors, I've updated my BIOS, etc... The only suggestions I can't seem to try are disabling fast-boot and SRT and I can't see any options in the BIOS or in Windows relating to those.

When I choose "something else" during the install I can see the Windows partition (and recovery partitions) and the unallocated space no problem, but the installer just will not detect Windows 8. I suppose I could just manually create the Ubuntu partitions and select them and start the install, but I'm assuming if it can't detect Windows 8 there's no way that GRUB would be correctly configured to boot to it and I don't want to lose access to my Windows install.

The posts here: [http://www.linlap.com/acer_aspire_v7-582pg](http://www.linlap.com/acer_aspire_v7-582pg) and here: [http://www.linlap.com/acer_aspire_v7-482pg-9884](http://www.linlap.com/acer_aspire_v7-482pg-9884) are about systems with almost the exact same hardware config and don't mention having any such problems...so I'm not sure what could be going wrong with mine.

Does anyone have any other suggestions I could try?

---

### Post by Penguin360 on 2014-10-20
I am facing a similar issue except I was trying to install Ubuntu 14.04 with dual boot with Windows 7. My PC's DVD rom is out of order, so I boot into my USB DVD drive. The installer loaded fine except it could not recognize the existing Windows OS and gave the same message as yours. Have you tried to load the installer from the built-in DVD drive? I wish my DVD drive is working...

---

### Post by yancek on 2014-10-20
> When I choose "something else" during the install I can see the Windows  partition (and recovery partitions) and the unallocated space no  problem, but the installer just will not detect Windows 8.

Not really sure what your problem is here.  It detects windows partitions but not windows 8, do you have some other windows operating system installed that is identified?  If it is showing windows partitions, what makes you think they are not the windows 8 partition?  Boot the Ubuntu medium and select the "Try Ubuntu" option and when you get to the Desktop open a terminal and enter the following:  sudo gparted

That will show your drives/partitions and some other info which might help someone understand what the problem is if you post it here.
Is your windows 8 pre-installed?  Is it using UEFI/GPT to boot?

---

### Post by oldfred on 2014-10-20
Some more links on Aspire systems.
 [http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

You probably just need to use Something Else. And that currently with Windows 8 is the only safe way to install as there is a bug where Windows may get erased as that is default install method, but instructions on screen are not clear. Always have a full backup of Windows and the efi partition.

More details in link in my signature.

      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Jesse_Taft on 2014-10-20
> **yancek said:**
> Not really sure what your problem is here.  It detects windows partitions but not windows 8, do you have some other windows operating system installed that is identified?  If it is showing windows partitions, what makes you think they are not the windows 8 partition?  Boot the Ubuntu medium and select the "Try Ubuntu" option and when you get to the Desktop open a terminal and enter the following:  sudo gparted

That will show your drives/partitions and some other info which might help someone understand what the problem is if you post it here.
Is your windows 8 pre-installed?  Is it using UEFI/GPT to boot?

As I said above, the installer *does *detect the partition that Windows 8 is on...never said it doesn't. But it doesn't detect Windows 8 to give me the option to install along-side it. There are no other operating systems installed...it's just the pre-installed Windows 8. It is using UEFI and as I said I've already attempted the install in both UEFI and Legacy mode. I'm not sure how to tell if it's GPT...but what would I do differently if it were? My gparted screenshot is below:
[ATTACH=CONFIG]257393[/ATTACH]

Could it possibly be because my Windows partition is labeled as Acer instead of Windows?

---

### Post by oldfred on 2014-10-20
Your Windows is installed in UEFI mode, which all Windows 8 pre-installed systems are. So you must have gpt partitioning since Windows only boots in UEFI mode from gpt partitioned drives.

Make sure fast boot or always on hibernation is off, usually better to have secure boot off.
Use Windows to shrink the Windows NTFS partition to make unallocated space and reboot Windows so it can run chkdsk and make its repairs to its new size. Make sure fast boot is off. Windows likes to reset to its defaults all the time.

Make sure you have backed up Windows & the efi partition. 

How you boot install media is how it installs UEFI or BIOS/Legacy/CSM:
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
    
The default install is just / (root) & swap, but better to have a separate /home anyway. And that requires you use Something Else to install. 

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

