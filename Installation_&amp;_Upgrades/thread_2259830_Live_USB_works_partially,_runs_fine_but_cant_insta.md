---
title: "Live USB works partially, runs fine but cant install"
date: 2015-01-07
forum: Installation &amp; Upgrades
---

### Post by Oral B Sonic Complete on 2015-01-07
Hi,

I have some trouble installing ubuntu 14.04 LTS on my asus r252b netbook. 

Here is what i hope to achieve: ubuntu as the only OS on my netbook. 

So i created a bootable usb on a 2GB flashdrive that i previously used to install ubuntu 12.04 on that very netbook. I remember having some trouble installing 12.04, but nothing specific. I created the bootable usb on the same machine with the same tools (followed instructions from canonical`s site and the GUI seemed familiar) as i did last time around. I added 40MB for persistent changes. I completely erased the HDD with gparted, tried partitioning it( which didn't help) and left it completely barren. 

It doesn`t work as it should, though.

The live stick allows me to try ubuntu about 50% of the time. at other times, it fails to load ubuntu correctly or doesn't work at all. I suspect that this may be a problem due to the laptop`s... difficulties with it`s usb ports. 
But whenever I try to install ubuntu, it doesn't work. Either the installer keeps showing error messages and ends up telling me that there isnt enough space to install ubuntu, or it straight up tells me that it doesnt have permission to install on my HDD. That is, if it doesn't freeze during the setup. 

I previously had win 8.1 on that netbook. 
The R252b has a 64bit amd apu. 

Help?
Thanks!

---

### Post by ajgreeny on 2015-01-07
If the machine has Win 8.1 it may have a motherboard with UEFI instead of MBR -BIOS; do you know which it is?

From the live USB please run ```
sudo parted -l
``` and report back here the output.

However, are you certain the .iso file you used to make the USB was a good download?  Check the md5sum with [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") and if it does not match you will have to download again, preferably with a torrent client, eg transmission, which checks the file as it arrives and gets new small packets if any are corrupt.

---

### Post by Oral B Sonic Complete on 2015-01-07
Holy.... wow. I hadn't  expected an answer until tomorrow. 
Well, it says it is an Asus Eee PC ACPI BIOS, so I would say BIOS, weren't it for the headline that claimed it is an Aptio Setup utility by American Megatrends. I remember vaguely that I read something about this and UEFI. 
It is capable of launching an EFI shell and detects the bootable flash drive twice, once as BIOS, once as EFI.
The EFI shell function doesn't work though.

---

### Post by Oral B Sonic Complete on 2015-01-07
Okay, so I redownloaded 14.04.1 on a win 8 system, formatted the flash drive using diskpart and reinstalled it using universal usb installer. hashes checked out fine, according to FCIV. 
Result: my bios doesnt even show up, I instantly got a screen asking me what I wanted to do, either install ubuntu or do a lot of other things. 

Now, the result of Sudo parted -l follows.

---

### Post by Oral B Sonic Complete on 2015-01-07
> 
ubuntu@ubuntu:~$ sudo parted /l
Error: Could not stat device /l - No such file or directory.              
Retry/Cancel? cancel                                                      
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD3200BPVT-8 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


Model: BUFFALO USB Flash Disk (scsi)
Disk /dev/sdb: 2072MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      65.5kB  2072MB  2072MB  primary  fat32        boot, lba



This is what I got. I|ll attempt to install once more and report on how it went. The live stick is a LOT more responsible than last time around.

---

### Post by Oral B Sonic Complete on 2015-01-07
Okay, I'm writing this from my laptop. It worked, although ubuntu seems somewhat sluggish when compared to the live stick. weird. i should probably turn of home folder encryption. 
Thanks a lot for the help! 
As for my previous post, i meant to say that the live stick is a lot more responsive, not responsible...

---

### Post by sudodus on 2015-01-08
When Ubuntu is sluggish, I suggest that you try the same engine with a lighter desktop environment, ***Xubuntu*** (medium light) or ***Lubuntu*** (ultra light). Stay with the version 14.04.1 LTS (long time support).

 			 			[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

