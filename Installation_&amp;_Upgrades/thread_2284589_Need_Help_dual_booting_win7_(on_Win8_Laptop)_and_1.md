---
title: "Need Help dual booting win7 (on Win8 Laptop) and 14.4.1 LTS"
date: 2015-06-30
forum: Installation &amp; Upgrades
---

### Post by subcook on 2015-06-30
[COLOR=#333333]I've set up many OS's on a single HDD in the past but have never run into this.[/COLOR]

[COLOR=#333333]Summer of 2013 I bought a laptop, Toshiba Satellite L855-S5383, i5, 650GB HDD, 8GB Ram and did not care for win 8/8.1. I wiped the HDD, made the necessary changes to the BIOS settings and installed Win7 Ultimate w/ Windows CD and everything was fine (note everything here is 64 bit).[/COLOR]

[COLOR=#333333]With the anticipation of Win 10 coming out, I quickly realized that I had best get Linux on this laptop as well.[/COLOR]

[COLOR=#333333]I shrunk the windows partition, reboot, than ran chkdsk, boot off the CD thinking I could use the ubuntu install wizard, and when it came to partitioning it said "....does not recognize current OS..." and showed my entire HDD as free space. I went back ang formatted the partition and tried it raw, I formatted NTFS, and the same result.[/COLOR]

[COLOR=#333333]I threw in gparted and it also does not recognize anything anywhere on the HDD.[/COLOR]

[COLOR=#333333]I also loaded into BIOS to see if I could adjust those settings again from when I ditched Win8, and they are no where to be found (UEFI I believe). I did this thinking that when I installed Win7, maybe there would be a booting issue, as I know the booting world changed w/ Windows with the release of Win 8 (again, UEFI I believe - still not very clear on it, guess Windblow$ wants to be even more anti-social). There was also an indicator in the ubuntu partition setup tool during installation that said the disk had GPD (or GTD) signatures were on the disk but something was deleted ..... I have no clue what this is, but have a hunch that this is an initial boot situation......meaning that my MBR is either trashed, or non-existent.[/COLOR]

[COLOR=#333333]Right now my HDD has the 100MB Reserved partition, my Windows Parition, and 250-300GB partition set aside for unbuntu.[/COLOR]

[COLOR=#333333]My goal is to have the reserved, win7, / (50GB) , 2-3GB Swap, /home (150GB)[/COLOR]

[COLOR=#333333]Does it have to do with the MBR, or the absence of .....?[/COLOR]

[COLOR=#333333]However I end up fixing this, will I have to go through the same process again when I put OpenSuSE on ?[/COLOR]

[COLOR=#333333]Thanks in Advance ![/COLOR]

---

### Post by oldfred on 2015-06-30
Pre-installed Windows 8 is UEFI with gpt partitioning.
Windows 7's default install is BIOS with MBR partitioning. You have to copy install from DVD to flash drive and move some efi boot files to correct place to make it a UEFI installer. How you boot installer (UEFI or BIOS) is then  the boot mode you have on hard drive.

But when Windows 7 installs in BIOS mode it converts drive from gpt to MBR and does it incorrectly. It seems Windows does not care about gpt's backup partition table (one of its advantages). So you have MBR but also have a backup gpt partition table. Most Linux tools see both MBR & gpt and assume drive must be totally repartitioned/reformatted.

You can easily fix by removing backup gpt partition table or reinstall Windows 7 in UEFI boot mode.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

You do need to have both Windows & Ubuntu in same boot mode, both UEFI or both BIOS.
      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by subcook on 2015-07-01
Thanks !  That helped.  I solved this by actually using the opensuse 13.2 rescue .iso :

[COLOR=#333333]If you have a USB available:[/COLOR]

[COLOR=#333333]Download the 13.2 live rescue CD. Maybe 13.1 would work for that, too.[/COLOR]

[COLOR=#333333]Burn to the USB. Then startup Yast.[/COLOR]

[COLOR=#333333]Install "gptfdisk-fixparts". That should install to persistant space on the USB.[/COLOR]

[COLOR=#333333](You could probably burn to a CD instead. But the install of "gptfdisk-fixparts" will be temporary, and will disappear on reboot).[/COLOR]

[COLOR=#333333]Then run the "fixparts" command against your disk.[/COLOR]

[COLOR=#333333]Here's the problem you are having:[/COLOR]

[COLOR=#333333]Your computer came with UEFI and the Win 8 install used GPT partitioning on the disk.[/COLOR]

[COLOR=#333333]You apparently switched to BIOS mode and legacy partitioning, to install Win7. But GPT partitioning is pernicious. Traces of the GPT partitioning table are still there, and "parted" and "gparted" do not like that.[/COLOR]

[COLOR=#333333]The "fixparts" command can remove all remaining traces of GPT partitioning.[/COLOR]

---

### Post by oldfred on 2015-07-01
Glad you resolved it.
I am sure that is the same fixparts, but have not used nor know about OpenSuse.

---

