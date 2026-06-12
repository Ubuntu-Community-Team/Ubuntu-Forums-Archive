---
title: "Dual boot Windows 8 + Ubuntu"
date: 2014-05-31
forum: Installation &amp; Upgrades
---

### Post by Rushyang on 2014-05-31
Bonjour Guys!


I have big time problem setting up Ubuntu 14.04 with Windows 8. I tired to search web a lot for this. But couldn't find the solution.


I have HP Pavilion G6 Laptop where I want to setup this. I have disabled UEFI in bios and activated Legacy mode. 


Now, 


1) When I install windows 8 first in just 1 parition (and leave rest of the space untouched), Ubuntu installer doesn't recognize any existing Windows 8 Environment and it gives me my whole 1TB of hard drive blank!


2) After wiping the whole hard drive, when I install ubuntu first, it installs using GPT parition table and windows doesn't let me touch any unused space for installation.


3) When I install ubuntu first with making "EFI boot partition" with the size of 500MB, windows doesn't recognize anything and shows everything as Unused space.


I also believe that Ubuntu only supports UEFI Boot parition because when I try installing without it it gives me an error.


Please advice how to install both of them and end up with successful dual boot.

---

### Post by LastDino on 2014-05-31
Always install WIndows first. And then Linux. 

Also, read this > [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

That post is quite well described. There are other sources which should be read too, like >
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by oldfred on 2014-05-31
You just have to be consistent. 
How you boot installer either UEFI or BIOS is how it installs.
And Windows only install to gpt partitioned drives with UEFI.
Both Windows and Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.
Ubuntu will boot in BIOS or UEFI mode from gpt partitioned drives.

So always boot in UEFI if that is what you want. And turn off legacy/BIOS/CSM mode in UEFI. Or turn off UEFI and turn on Legacy and only install in BIOS mode.
But you may have to convert drive to correct partitioning first.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by Rushyang on 2014-06-01
Thanks for your reply! I really appreciate it.

As you mentioned, I know that if we turn off UEFI and turn on legacy support then Windows will always install Boot loader information in MBR. But the thing is, here Ubuntu installer's behaviour is really surprising!

Even after installing Windows first and trying to install ubuntu, It does not recognize any previous installation and Paritions! It recognizes whole HDD as blank!

And when I install Ubuntu first then Windows Installer tellls me that previous partitioning table type is: GPT and windows can't be installed on any of the partitions.

---

### Post by oldfred on 2014-06-01
If you install Ubuntu in UEFI with gpt partitioning you must install install Windows in UEFI mode. In BIOS mode it will give that gpt error as it cannot boot with BIOS from gpt. So you must boot Windows in UEFI.

UEFI menu should show Windows 8 with either UEFI or BIOS. If Windows 7 the DVD is BIOS only and can be copied to a flash drive and updated to be a UEFI installer.

If your Windows is BIOS only, then convert gpt to MBR and install Ubuntu in BIOS mode.

Install Windows first in the mode you prefer either UEFI or BIOS. But then you must shrink Windows using its Disk tools and reboot. Then make sure fast boot or always on hibernation is off as that is usually why Ubuntu will not see Windows.
It also may not see Windows as if drive was gpt, Windows does not correctly convert drive to MBR. It leaves the backup gpt partition table so Linux tools see both MBR & gpt and does not know what you really want.
You can use fixparts to remove gpt data if necessary.

---

### Post by Rushyang on 2014-06-02
Thanks again Oldfred!

Yes, you are absolutely right.. I observed that Windows created backup of existing GPT in the Partitioning table and than wrote a new MBR.

I guess I can remove whole partitioning table with the gdisk right? If yes, then I can wipe the whole HDD and install the windows again. I guess there is something wrong with my bios because it doesn't detect CD/USB while I activate UEFI (and disable Legacy) and try to install Windows. So I will continue with Legacy BIOS and install fresh windows copy. Then disable Fast Boot and Hibernate option in windows and see if Ubuntu can detect installed Windows version to make dual boot.

I will report back again once it's done. Really appreciate your support! :D

---

### Post by oldfred on 2014-06-02
I thought Windows 8 would boot in UEFI or BIOS, but not used it myself.
And I do know that Windows 7 DVD only boots in BIOS, and you have to convert it to flash drive and do a couple of updates to make it work for UEFI.

---

