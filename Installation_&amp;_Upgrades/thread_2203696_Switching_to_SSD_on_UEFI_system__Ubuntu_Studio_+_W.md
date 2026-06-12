---
title: "Switching to SSD on UEFI system / Ubuntu Studio + Windows 7 dual boot"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by Arturas_Bajoriunas on 2014-02-04
Hello, people, 

So here I am with my HP G6 laptop who's hard drive is about to fail some time soon or not.. At least the system tells me that every time I switch on my laptop. I've decided to ditch preinstalled windows 8 and created new partition table and installed ubuntu studio. Then changed it to opensuse. Now want to go back to ubuntu studio.
Since my hard drive threatens me to fail, I've decided to get myself a solid state drive. (Any suggestions? I'm not needy about capacity. Just want it to be REALLY fast)  
My question is - where exactly is that UEFI stored? Will my laptop turn to Legacy with new drive installed? Or do I have to configure my new SSD to work with my laptop?
My goal is to dual boot ubuntu studio and windows 7 or at least ubuntu studio. Neither of them requires system to be UEFI, can I get rid of it somehow as it complicates the installation proces. 
For example I can only boot to grub2 command prompt and have to load kernel manually, no matter what I did I can't figure out, how to make grub load selection menu.

---

### Post by oldfred on 2014-02-07
Best to only have either UEFI or BIOS for both systems. 
Windows 7 only installs in BIOS from DVD, but you can copy to flash drive and modify it to boot in UEFI mode.
How you boot install media for both Windows & Ubuntu is how it installs.

If drive was originally Windows 8 with UEFI then it was partitioned with the newer gpt. But Windows 7 in BIOS mode will convert back to the old MBR, but leave the backup gpt partition table. Then all Linux tools see MBR and gpt backup and do not know what you have or want. 
If converting to BIOS with MBR, you will have to remove backup gpt partition data with fixparts.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Windows 7 will not be secure boot which simplifies a lot. And it does not have the always on hibernation which also makes it less complicated to dual boot.
      
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

With Ubuntu best to know which way you have booted as you need to be consistently UEFI or consistenly BIOS.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I was going to build a new system 2 years ago, but bought a 60GB SSD and my mostly 6 year old system works so quickly that it is difficult to justify new system. I have most data on large rotating drive, so I have two / (root) partitions of 27GB on SSD, one current install and one future/test. I used gpt and included space for an efi partition so I could move SSD to new system, but now it is older and not as fast as new ones, so not sure now. But my SSD only has Linux. If using Windows on SSD you have to use UEFI if gpt partitioned or use BIOS if MBR partitioned. Only Linux will boot from gpt partitioned drives with either BIOS or UEFI.

       [https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

