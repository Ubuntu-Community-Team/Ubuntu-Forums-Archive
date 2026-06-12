---
title: "Install Ubuntu with Windows 7 2 drives"
date: 2013-09-21
forum: Installation &amp; Upgrades
---

### Post by courtney2 on 2013-09-21
Hi! I'm new to Ubuntu and trying to do a dual boot system. I have Windows 7 as my main boot drive (SSD) and I'm trying to install Ubuntu 13.04 separately on a second hard drive. The problem is that Ubuntu won't boot and I don't get GRUB popping up to select which OS I want to run. Here is the message I get after doing the recommended boot repair: "[FONT=arial]GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again." How would I go about fixing this in GParted? What values would I enter? Here is the paste thing I got. [/FONT][http://paste.ubuntu.com/6136273/](http://paste.ubuntu.com/6136273/) Thank you in advance for your help

---

### Post by Jonathan Precise on 2013-09-21
Do you have UEFI? If so, then you must use ubuntu 64-bit (if you need 32-bit, mark yourself as affected by these 2 bugs:
[Bug 1]("https://bugs.launchpad.net/boot-repair/+bug/1228717")
[Bug 2]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1025555"))

If you do NOT have UEFI, then use GParted to make a new unformatted partition (1 MB). Then apply. Right-click the new partition and select "Manage flags". Add the "bios_grub" flag. Click ok. Exit. Run boot-repair again. Post results and the pastebin link.

---

### Post by oldfred on 2013-09-21
Since you are booting Windows in BIOS mode, you really do not want to install Ubuntu in UEFI mode. But using gpt in BIOS mode is fine. I have XP on a MBR drive and since 10.10 have booted Ubuntu from a gpt drive in BIOS mode. But you have to have the bios_grub partition for grub to install correctly for BIOS boot. Partition can be anywhere on drive (only efi partition needs to be first or near beginning of drive). Follow directions posted by Jonathan Precise. Then be sure to install grub2's boot loader to the Ubuntu drive and change BIOS to boot that drive.

---

### Post by courtney2 on 2013-09-22
I downloaded the 64-bit option and when I installed Windows, it was installed in UEFI mode and I'm trying to install Ubuntu in UEFI as well. Just because I think I have it confused, what is an EFI partition? Does it have anything to do with UEFI? Also what does GPT stand for? Just so you guys know, I am really new at this and probably taking bounds beyond my knowledge by doing this dual boot system. Would it be bad to run GParted with UEFI?

---

### Post by oldfred on 2013-09-22
Your pastebin shows Windows in BIOS boot mode with MBR(msdos).

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)


 gpt(GUID) is required for drives over 2TB, suggested for SSDs, and required for UEFI booting. Ubuntu will work with gpt partitioned drive with either BIOS or UEFI.

    Windows will only boot from gpt partitioned drives with UEFI.
Windows x64 Installer determines which firmware has been used for booting the ISO/DVD/USB. If BIOS is used, only MBR is supported. If UEFI is used then only GPT is supported. Not vice-versa.

---

### Post by courtney2 on 2013-09-22
So I have to install ubuntu in BIOS then right? How would I do that since it looks like Ubuntu wants to install in UEFI? Also, if I got a new motherboard in the future that was UEFI, would I have to redo my drives? Also could I simply fix this problem just by creating that boot partition?

---

### Post by oldfred on 2013-09-22
All my new drives (that are not Windows), I partition with gpt and put an efi partition at the beginning even though my BIOS cannot use it. And since I have BIOS I also have a bios_grub partition for grub to install correctly with gpt and BIOS. Then I can move drive to UEFI system and add grub boot files to efi partition and have it work.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu - Post #6 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by courtney2 on 2013-09-22
Okay so I have an empty 500GB I'm dedicating to Ubuntu. So here is a thought on what I should do.

250MB efi FAt32 w/bootflag
1MB w/bios_grub flag (I don't recall seeing that option during the install process)
15GB Mountpoint / primary ext4
I won't use hibernate, but should I still create an 8GB swap point?
Then 400GB /home ext4 
Leave whatever remains non formatted. 

How does that sound for what I'm trying to do?

---

### Post by oldfred on 2013-09-22
If not hibernating and you have 8GB of RAM I might suggest just 2GB to have some swap. Some say it works without any, but I like to have a little just in case.Since you have 500GB, I might make / 20GB. I find if I write a standard DVD it uses 4GB in /tmp so having some extra is again not essential.

I think now if installing in BIOS mode it creates a bios_grub automatically. Back when I use 10.10, if you did not have it created in advance it would not install grub to MBR.
I like to have a little room for another 20GB for a second / so you can test next version if desired. Or have a NTFS data partition for data you may want to share with Windows. Or you can add that to your Windows drive. I prefer with Windows to only mount Windows system drive as read only, and have a separate NTFS data partition set read/write for shared data.

If using gparted you have to change it from default MBR(msdos).
  I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning

---

### Post by courtney2 on 2013-09-24
I'm going to go with a complete reinstall. I want to get it right rather than mess with the partitions after the install. So I'll make a /20GB and my swap 2GB. Since it seems like Ubuntu wants to install in UEFI, can I force it into installing in BIOS (Asus P8B75-v). If it's installing bios_grub automatically, then do I not have to create a /boot partition? So perhaps instead I'll create a /home partition, and maybe a 50GB NTFS partition...I'm just confused about why Windows 7 installed in BIOS, but it seems like Ubuntu wants to install in UEFI..makes no sense because I thought it was one or the other?

---

### Post by oldfred on 2013-09-24
It totally is what you choose in UEFI/BIOS on how to boot. But I think you have to convert Windows 7 to a flash drive and make a few minor changes to get it to install in UEFI mode. Ubuntu DVD boots either way. This shows both screens so if you get UEFI try a different entry in UEFI boot menu for flash drive.
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by courtney2 on 2013-09-26
Okay guys I solved the problem! So here's what I did. When I installed Ubuntu I just did a /, /home and swap area. Then I accessed Ubuntu via liveCD and installed and ran boot repair and this time it fixed the problem. Now I get the GRUB boot loader after post and I can choose which drive I want :) thank you guys for the help!

---

