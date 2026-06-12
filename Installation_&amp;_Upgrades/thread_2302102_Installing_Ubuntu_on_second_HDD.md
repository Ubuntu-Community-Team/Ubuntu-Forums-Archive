---
title: "Installing Ubuntu on second HDD"
date: 2015-11-07
forum: Installation &amp; Upgrades
---

### Post by rick51 on 2015-11-07
[FONT=&amp]Hello
[FONT=&amp]I know there have been several threads related this topic, however I cannot find a full answer.
[/FONT][/FONT]
  [B][FONT=&amp][I]My System
[/I][/FONT][/B][FONT=&amp]Is an Asus P5Q Pro Turbo motherboard with 8Gb ram and Windows 10 new install and not a upgrade.
[/FONT][FONT=&amp]
I do not want to get in to any trouble as I&#8217;m new to Linux, I have Windows 10 installed on a 1tb HDD which has 4 partitions (C,D,E,F).
 [/FONT]
  [FONT=&amp]I would like to install Ubuntu 14.04 on to a second new 2tb HDD, with the ability to boot to Ubuntu or Windows 10 from a boot menu as I do not know about Grub. 
[/FONT]
  [FONT=&amp]I would like to use Ubuntu to backup 3 Windows PC, [/FONT][FONT=&amp]Samba as print server,[/FONT][FONT=&amp] maybe Xbmc and to learn about Linux and at some stage change to Linux as my main system.

Rick51
[/FONT]

---

### Post by grahammechanical on 2015-11-07
And your question?

I think that this is still applicable.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

In Linux the first hard disk is called sda (sata drive a), the second hard disk is called sdb. If Windows 10 is installed on sda then you need Ubuntu to be installed on sdb. Here is something to watch out for: The Ubuntu installer will default to installing a boot loader (Grub) onto sda. It is best to change that to sdb. Then you can use the BIOS/UEFI to select which hard drive to boot from. If you set it to sda then Windows 10 will load. If to set it sdb then you will get a boot menu that will let you load either Ubuntu or Windows 10.

You choose the Something Else option and at the partitioning screen you select sdb and the click Change. At the dialog you set Use As to Ext4 from the drop down menu. You tick the box to format and set the mount point to / from the drop down menu.

Underneath the main partitioning window there is a panel where we can select the location the boot loader is to go. Scroll down the list and select sdb. That is important. And this process will give you a Ubuntu install of two partitions, one for Ubuntu and one for swap. And a boot menu that lets you load either Ubuntu or Windows. If for any reason the Ubuntu boot loader gets broken you will still be able to load Windows by entering the BIOS/UEFI to set the boot loading to sda.

If you want a more complicated partitioning scheme for Ubuntu, then that is another question.

Regards.

---

### Post by oldfred on 2015-11-07
Did you install Windows in UEFI or CSM/BIOS/Legacy boot mode?
You want Ubuntu in the same boot mode.

If UEFI see lots of useful links in the link below in my signature.
It may be better to disconnect Windows drive, but you want an ESP - efi system partition on your Ubuntu drive. But with UEFI grub only installs to the drive seen as sda or probably your Windows drive's ESP. With UEFI they share ESP without issue.

---

### Post by rick51 on 2015-11-08
Thanks for the pointers. The motherboard has a standard BIOS not UEFI. So would it be best to disconnect Windows drive and plug-in the new 2tb drive and install Ubuntu then reconnect the windows drive and go in to BIOS and set to boot from Ubuntu drive? Do i only need to two partitions which Ubuntu will steup at install?

---

### Post by oldfred on 2015-11-09
Standard installer only creates the two partitions, / (root) and swap. But it has done that since the beginning of Ubuntu when a large hard drive was 120GB and most desktop installs were dual boot.
But you really do not want a 2TB /. 
And if you may get a newer UEFI system in future I would partition Ubuntu drive as gpt. Windows only boots from gpt with UEFI, but Ubuntu will boot in either BIOS or UEFI mode if correct partitions are on drive. And ESP - efi system partition should be nearly front of drive.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
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

