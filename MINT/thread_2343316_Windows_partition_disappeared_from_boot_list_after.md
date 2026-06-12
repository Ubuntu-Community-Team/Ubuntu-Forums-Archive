---
title: "Windows partition disappeared from boot list after reinstalling Linux Mint"
date: 2016-11-15
forum: MINT
---

### Post by triedandtested2 on 2016-11-15
Hey all.

I've been racking my brain over this and just can't seem to find any help or solutions online.

Alright,  so here's the problem. I've got my computer dual booted with Windows 10  and Linux Mint 17. Everything has been totally fine for months - I got  it all set up at the end of last year. Then brilliant me decided I  needed to reinstall Mint (I think I accidentally deleted some important  files or something) but after a successful reinstallation, my windows  partition had disappeared from the boot list. I was very careful not to  do anything to that partition during setup that would cause it to  reformat or harm it in any way, but now instead of the usual Windows 10  boot option I get Windows Recovery Environment, which just sends me to a  black screen with an endlessly blinking cursor.

The Windows  partition is still there, untouched, all files in place. It's just not  being recognized in the boot list anymore, for some reason.

sudo os-prober returns the following:
  No volume groups found
/dev/sda1:Windows Recovery Environment (loader):Windows:chain



and sudo update-grub returns:[l]("https://forums.linuxmint.com/viewtopic.php?f=46&t=233750#")
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
Found Windows Recovery Environment (loader) on /dev/sda1
done



My windows partition is found at /dev/sda2.

So basically, my question is how do I get my windows partition to be recognized in / added to the grub boot list?

Thank you!!
--Tried and Tested

---

### Post by howefield on 2016-11-15
Moved to the "*MINT*" sub forum.

---

### Post by oldfred on 2016-11-15
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by triedandtested2 on 2016-11-15
Here's the URL from Boot-Repair:

[http://paste2.org/N3An7Nj5](http://paste2.org/N3An7Nj5)

---

### Post by yancek on 2016-11-15
You have a standard MBR install for Mint/windows and Grub code in the MBR.  Unfortunately, you also have Grub code on sda1 and sda2 which are windows ntfs partitions and should not happen.  I don't think Grub will install to an ntfs partition without intervention but...?  There are comments in the boot repair output about GPT partitioning and my understanding is that windows with GPT needs UEFI which you don't have.  Not sure how you would repair this but you might try an online search on how to correct these problems.  Hopefully oldfred or someone more familiar will come along with a suggestion or two.

You do have your 3 windows partitions, probably a small boot partition with a system and recovery partition.

---

### Post by oldfred on 2016-11-16
You never install grub to the partition boot sector [BS] of NTFS partitions. Windows has vital boot info in those boot sectors.
But NTFS has a backup and you can usually just restore from the backup.
 You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510) 

It used to be that Ubuntu would not install to a drive with both MBR & gpt data. When you install Windows in BIOS/MBR mode to a previous UEFI/gpt drive, Windows incorrectly converts from gpt to BIOS. It leaves the backup gpt partition table and then Linux partition tools get confused if you have MBR or gpt, so want to just totally repartition  & reformat drive.


 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

---

