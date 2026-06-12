---
title: "GRUB rescue console"
date: 2013-04-14
forum: Installation &amp; Upgrades
---

### Post by dutchmarco on 2013-04-14
Hi all,


I wanted to install Ubuntu (or Suse, or ..., even tried - and failed - Win7) on my new Seagate 3TB HD which I now suspect is a bit wonky. I though I had succesfully installed Ubuntu 12.04.2 (286) LTS, with my entire HD all to itself. At first I tried a fancy partitioning scheme for dual boot, but I kept having problems with that (I forgot the GRUB message, but I ended up on the rescue prompt. So my latest attempt at Linux was Ubuntu with all 3TB to itself.


Today I powered on my PC and instead of booting to the Ubuntu-desktop, I ended up in the GRUB2 (iirc this is v2) rescue console, following the error message of Out of disk. not knowing any commans\ds to type, I tried ```
help
``` and ```
?
```, both commands were not recognized, So I jumped on the Googol and foundI might try ```
ls-l
```. Sure I tried that, but ls was unrecognized too!


What do y'all think? Do I need to replace my new HD or is there something else wrong (with GRUB, or my Motherboard [Abit AB9 Quad]) or something else?)

---

### Post by oldfred on 2013-04-14
It is ls -l or it has a space between the command ls and the parameter -l as most commands in Linux do.

With a 3TB drive it has to be gpt partitioned. Is this an internal drive as we have seen some USB drive boxes not work with USB3 or 3TB drives.

I am not sure that a grub_bios partition will be correct in a dual boot configuration or just you may have issues which install has used it.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

