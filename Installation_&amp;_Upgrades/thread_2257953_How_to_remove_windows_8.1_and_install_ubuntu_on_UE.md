---
title: "How to remove windows 8.1 and install ubuntu on UEFI computer"
date: 2014-12-23
forum: Installation &amp; Upgrades
---

### Post by pvtillo on 2014-12-23
My computer supports UEFI.

I like to remove windows 8.1 (preinstalled) and only install Ubuntu 14.04.

With older computers just with BIOS, I deleted all partitions and installed Ubuntu on a new partition.

How do I do that with a Computer with UEFI instead of BIOS?

---

### Post by oldfred on 2014-12-23
You can do the same thing.

But best to decide a few things first. 

Do you want UEFI or BIOS? Generally with newer systems UEFI is better, but  a bit more complicated.
But even with UEFI hardware and installing BIOS/CSM boot mode you have to make several UEFI/BIOS settings. So it is a bit more complicated with BIOS on UEFI hardware.

How do you want to partition drive? 
With BIOS your only choice was the now 35-40 year old MBR(msdos) partitioning. 
Now with Ubuntu you can use gpt with either UEFI or BIOS. Windows only boots from MBR with BIOS and Windows only boots from gpt with UEFI, so if their is the slightest chance you want Windows back, you will need UEFI/gpt.
Even if reasonably sure you do not want Windows best to make a full backup of efi partition and Windows. Many find one application that only runs in Windows they have to have, or later want to sell system and it must have Windows.

Do you want the default of just / (root) and swap or added partitions like /home or data partition(s)?
If you just want defaults all around you can just install. Not sure if it will use gpt or MBR, but it will create just / & swap.

Best to have secure boot off. You need to then set UEFI/BIOS to boot mode you want and be sure too boot flash drive in that boot mode. How you boot install media is how it installs. 
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

