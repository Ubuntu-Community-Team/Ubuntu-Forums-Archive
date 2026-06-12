---
title: "ubuntu 15.04 -- installation stalls"
date: 2015-03-27
forum: Installation &amp; Upgrades
---

### Post by xigen on 2015-03-27
Ideally I would get Windows 8.1 and Ubuntu 15.04 to dual boot on my UEFI -- Gigabyte GA-970A-UD3P   F1 bios system. 

Windows 7/8 because of:  Rocksmith, EarMaster, Excel, Word

Ubuntu 15.04 because of:  Focusrite 6i6 and support under kernel 3.19

..................

Ubuntu 14.04 was working really well on my system and I backed up /home as well as using APTIK to save my settings/package list.  

When I used the new 15.04 disk to 'try' 15.04 64 my system ran fine.  Though networking (Realtec chip) did not work.  

I tried to install 15.04 alongside 14.04 -- and the 15.04 install froze.    

I finally got 15.04 installed - and, unfortunately upon booting all I got was blank screen (no prompt, no ability to open a terminal).

I tried to go back to 14.04 --  the 'demo' worked -- unfortunately when I re-installed 14.04 64  I got a blank screen and no terminal access

..................

I then tried to install Windows 7 SP1 

Please double check my process  here:
1) use 14.04 disk / gparted to remove partitions
2) use gparted to reformat disk to ntfs
3) Install Windows 7 SP1
4) Get the 14.04 disk, and install 14.04 with windows
4.5) perhaps use boot repair if there are boot issues

After removing partitions and formatting the SSD for ntfs I tried to install Windows 7.  The install got to the first screen and froze.  No mouse / no tab/ no keyboard interaction.

.........................

My questions:

What is the correct process for installing Windows 7 on  a  disk  which had ubuntu 14.04?

How can I get ubuntu 14.04 or 15.04 to install?

Is this a bios issue to take up with Gigabyte?   Is it time to reflash the bios?  

Thoughts?

---

### Post by Vladlenin5000 on 2015-03-27
> What is the correct process for installing Windows 7 on  a  disk  which had ubuntu 14.04?

The same as installing in a blank disk or any other disk with any other contents on it. Why would it be different?

---

### Post by oldfred on 2015-03-27
If underlying partition structure was gpt, then most Windows 7 installs convert to MBR(msdos) and do it incorrectly. 
You have to copy Windows 7 installer to flash drive and modify it to be an UEFI installer.
Or you have to convert left over gpt data that Windows did not correctly remove with fixparts.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[URL="http://www.rodsbooks.com/fixparts/"]http://www.rodsbooks.com/fixparts/

[/URL]
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)


Windows only boots in UEFI mode from gpt partitioned drives.
Both Windows & Ubuntu only boot in BIOS mode from MBR partitioned drives.

---

