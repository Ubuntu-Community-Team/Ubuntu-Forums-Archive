---
title: "Partitioning for EFI"
date: 2014-01-09
forum: Installation &amp; Upgrades
---

### Post by inhumangeek on 2014-01-09
I'm re-installing Ubuntu 13.10 (writing this from a LiveUSB session) as my upgrade from 13.04 didn't go according to plan (I wanted to get a fresh install anyway!). 

I wanted to take this opportunity to convert to EFI mode (or UEFI?) and am a bit concerned about creating the EFI partition - I want to make absolutely sure that I'm doing it correctly! I don't have dual boot or anything like that. I have seen other examples on the forums but these are mostly people who  want to dual-boot - this is not my situation and I want to make sure I have the answer for my exact  problem.

Setup:
sda1 is currently swap
sda2 is where I want to install Ubuntu (mounted as root ) - this can be wiped
sda3 has data I want to keep (although it is backed up to a cloud service )
sdc1 needs to be mounted as /home - I know how to do this (and have on a previous occasion successfully mounted my old home area during install)

What are the exact steps required to make space for the EFI partition without losing the contents of sda3?
Can I delete [swap + root] and replace with (EFI + swap + root)? What order should these be in?
Can someone explain precisely how to set up the EFI partition? I have read the Ubuntu documentation but I'm still not 100% (for example, what should the file system be (it says FAT32 yet there is a /boot/efi option in the installer) or whether or not I need to mount it explicitly.

My gparted is below - ignore the fact that sda2 is mounted as /mnt - I was trying to fix another problem.

[ATTACH=CONFIG]249341[/ATTACH]

Many thanks for any advice,
Paul

P.S. A bit of background:
My current installation attempt went a bit wrong and I got the grub error message described [here]("http://askubuntu.com/questions/386467/error-file-grub-i386-pc-normal-mod-not-found-in-ubuntu-13-10"), so I followed the instructions without success, experiencing errors similar to those discussed [here]("http://ubuntuforums.org/questions/392360") - which suggests that my installation is expecting an EFI partition, but I don't have one. I would like to use EFI (I think) if only to speed up boot times. The other option is to fix the grub errors but I would rather try to persue the EFI resolution if possible.

---

### Post by oldfred on 2014-01-09
You cannot easily convert. It looks like your drive is MBR(msdos) and UEFI only boots from gpt partitioned drive.
Windows only boots from gpt partition drives with UEFI. 
Both Windows & Ubuntu only boot from MBR drives with BIOS.
But Ubuntu will boot from gpt drives with either BIOS or UEFI, so I suggest if not using Windows for all new drives to use gpt partitioning.

You may be able to convert. And efi partition does not have to be large, so you could delete current swap and still have efi partition first. UEFI suggest it be first partition, but should be near beginnig of drive.

If thinking of converting be sure to have good backups. 
Systems know if you do not have good backups and make you make mistakes that delete data. But if you have good backups everything goes without issue. ;)

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
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
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by inhumangeek on 2014-01-10
OK thanks very much for those tips, I've never even heard of gpt! I assume I can use gparted or the installer to set up gpt partitions?
I have copied all my data off the drive so I don't need to worry about losing data - I will start from scratch.

How does the following look to you?
sda:
1. 300MB EFI
2. 1 MB BIOS (just in case I need this in the future)
3. 30GB ext4 (mounted at /)
4. all but 2GB ext4 (to be later mounted in fstab for my media server) 
5. 2GB swap

As I mentioned above my home areas are on a different HDD so this will be mounted as /home.

One final question - I thought swap space should be allocated at the start of the drive for performance reasons - so can I put the swap between 2 and 3 in my list above?

Thanks again

---

### Post by oldfred on 2014-01-10
Swap now is rarely required with newer computers. Back when you only had 256MB or 512MB you needed swap. But now with RAM usually 4GB or more swap is rarely used. And the difference in speeds on one part of drive and the other are nominal. 

If you are installing Windows in UEFI mode it has several partitions that are required. It will use the same efi partition. Best to install Windows first so it can create it partitions. Then shrink Windows with its own partition tools but never create partitions with Windows.

If installing Windows 7 you must convert it to USB install and slightly modify it for UEFI install. Standard DVD is BIOS only. Windows 8 is both as I understand, but installs in mode you boot installer or it installs in UEFI if booted in UEFI or BIOS if installer booted in BIOS, just like Ubuntu does.

---

### Post by inhumangeek on 2014-01-12
So I went ahead with the configuration I posted above and it all seems to be working fine.

Thanks again.

---

