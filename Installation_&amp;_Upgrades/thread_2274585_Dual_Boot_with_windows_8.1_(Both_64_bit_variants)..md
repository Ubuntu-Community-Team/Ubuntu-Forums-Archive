---
title: "Dual Boot with windows 8.1 (Both 64 bit variants)."
date: 2015-04-20
forum: Installation &amp; Upgrades
---

### Post by Todd_Ethersee on 2015-04-20
Hi all, I am looking for abit of advice on a dual boot installation I have planned.

First about about me and my background;

I have always used a variant of windows through the years and have dabbled in a couple of different distros of linux in the past. I now a little bit about linux from reading and a little bit of dabbling and can do basic installation.

Second about the computer in question;

CPU = Phenom II X6 1090T
RAM = 8GB (soon to be 16gb)
SSD = 120gb sandisk ultra II
HDD = 320gb generic
External HDD's = 1 x WD 1tb and 1 x WD my passport 320gb
Graphics card = ATI 5770 (soon to be Nvidia GTX 760)
Will eventually have server in the home which I would want to run NAS and shared printer functions amongst other things but that is probably not going to happen for another 6 months when the wife actually allows me to buy more hardware. So not vital but would like to keep in mind for the future.

Third what I would like to achieve;

I would like to have both windows and ubuntu on the SSD as follows;

Linux
The / partition I would like at 30gb.
The swap partition i would like at 32gb.

Windows
I would like this partitioned at 50gb+.

The HDD i would like as follows;

Linux
The /home partition i would like at 160gb.

Windows
I would the remaining 160gb for windows to access.

Then I would like to be able to use the 2 external drives via both OS's.


My question is the above possible and could someone point to some useful forum posts or even offer up some advice on the above.

Kind Regards and thank you for any help and advice in advance

Todd

---

### Post by oldfred on 2015-04-20
Yes.
What versions of Windows & Ubuntu?

Is this an UEFI system? And if so, do you want UEFI or CSM/BIOS.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    
What motherboard?
There are generic video drivers, and proprietary for AMD & nVidia. You will have to keep track and make sure correct is installed. Some work out of the box others require the proprietary drivers to work or work well.

If dual booting you should not hibernate. And then with that much RAM, you do not need a large swap. I would suggest 2GB just to have some. Others have posted they did not need swap at all. But it editing videos or similar then you may need all the RAM you can add and larger swap.

If using UEFI, then I would make sure all drives are gpt partitioned. But they do not have to be.
Windows only boots with UEFI from gpt drives, but all versions since XP read gpt partitioned drives.
Ubuntu can boot in either UEFI or BIOS mode from gpt partitioned drives if correct supporting partitions are on drive.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

Links to much more info on UEFI boot is in link in my signature below. Some is general good practice like backup so even if you want BIOS may be worth reviewing.

I would install Windows first, shrink the NTFS partition using Windows own tools and reboot immediately so it can run chkdsk and update to its new smaller size.
Make sure the Windows fast startup is off as that is always on hibernation. And if motherboard has UEFI fast boot best to turn that off, or set it so you can get into UEFI from keyboard not just from Windows.

      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Todd_Ethersee on 2015-04-21
> **oldfred said:**
> Yes.
What versions of Windows & Ubuntu?
[COLOR=#ff0000]Windows = 8.1 64bit.
Ubuntu = 64bit, not sure of version yet.[/COLOR]

Is this an UEFI system? And if so, do you want UEFI or CSM/BIOS.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
[COLOR=#ff0000]it is not a uefi system.[/COLOR]
    
What motherboard?
[COLOR=#ff0000]m4a785td-v evo[/COLOR]
There are generic video drivers, and proprietary for AMD & nVidia. You will have to keep track and make sure correct is installed. Some work out of the box others require the proprietary drivers to work or work well.

If dual booting you should not hibernate. And then with that much RAM, you do not need a large swap. I would suggest 2GB just to have some. Others have posted they did not need swap at all. But it editing videos or similar then you may need all the RAM you can add and larger swap.
[COLOR=#ff0000]Noted.[/COLOR]

If using UEFI, then I would make sure all drives are gpt partitioned. But they do not have to be.
Windows only boots with UEFI from gpt drives, but all versions since XP read gpt partitioned drives.
Ubuntu can boot in either UEFI or BIOS mode from gpt partitioned drives if correct supporting partitions are on drive.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

Links to much more info on UEFI boot is in link in my signature below. Some is general good practice like backup so even if you want BIOS may be worth reviewing.

I would install Windows first, shrink the NTFS partition using Windows own tools and reboot immediately so it can run chkdsk and update to its new smaller size.
Make sure the Windows fast startup is off as that is always on hibernation. And if motherboard has UEFI fast boot best to turn that off, or set it so you can get into UEFI from keyboard not just from Windows.

      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)


Thank you for the above, great starting points and i will read up on them. I have answered your questions in red above.

Kind Regards

Todd

---

### Post by oldfred on 2015-04-21
You then have to use MBR(msdos) partitioning for the drive with Windows. 
If there is any chance the other drives might get moved to a new system that would be UEFI, then I might use gpt so I did not have to repartition & reformat them then.

I would install Windows first and it will use two of the 4 primary partitions. I would make the third primary partition the extended partition which then can have as many logical partitions as you want. 

Detail Something Else guides are good for BIOS or UEFI type installs. In both cases you choose on partition screen which drive to install grub2's boot loader normally sda which is default.

---

