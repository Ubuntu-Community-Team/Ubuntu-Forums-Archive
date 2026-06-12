---
title: "How to restore boot partition after removing via Grub Customizer"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by AnyMation on 2015-04-18
I have 3 versions of Ubuntu (1X 12.04 and 2X 14.04).  I installed the 2nd 14.04 after the first one had some hiccups during the installation. A subsequent problem was that I could not get the good 2nd 14.04 installation to be my *default* at startup. (I previously was able to do it)

I tried everything, and even tried editing the list configuration via Grub Customizer... nothing worked. I eventually decided to remove the initial 14.04 (faulty) installation via Grub Optimizer. Grub Optimizer only *marked it* as removed but did not actually remove it, but it still did not work (I can't remember the details: it was quite a while back).

The only way I was able fix the default boot version was to un-install and re-install grub itself. That worked and solved the default boot version... but now I found that (due to the "remove" in Grub Optimizer) my *correct* version of 14.04 was missing. I am only able to boot into the faulty 14.04 or old 12.04. (It may be my fault: I might have been tired and accidentally removed the wrong 14.04 - I don't know.)

However: both 14.04 partitions are still there, so I suppose that the boot script of correct 14.04 has been deleted/corrupted.

**Question**: Is there any way I can still fix or create a boot script so that I am able to get boot into the correct 14.04 that should still be available on the partition?

If I understand correctly, I think the correct 14.04 is on partition /dev/sda7 and the faulty one on /dev/sda6.

A word of warning: I am a greater Ubuntu enthusiast than I am knowledgeable about Ubuntu and Linux. Although I have been using it for a few years and been able to resolve quite a few problems, I rely heavily on the knowledge (and intelligent monkey-see, monkey-do :-) ) that I obtain from the Internet.

I am trying to avoid another 14.04 re-install, customization and configuration, and installing of a multitude of applications - as they are all available in the correct 14.04.

Thanks in advance.

---

### Post by yancek on 2015-04-18
Can you mount the Ubuntu 14.04 you are unable to boot from one of the other Ubuntus?  Take a look at the boot/grub directory to see if all the files are there.  Run:  sudo update-grub and watch to see if you get a new entry for sda7.  If it shows, it should be on the boot menu when you reboot so just select it.  If you don't have the grub files, that's another problem.

---

### Post by AnyMation on 2015-04-18
Yancek, being a bit of a novice, I am not sure which files should all be in the boot/grub directory. But I ran sudo update-grub, and it only shows the 14.04 on /dev/sda6 :-( (that is, apart from the 12.04 it also shows)

---

### Post by AnyMation on 2015-04-19
Any more suggestions perhaps?

---

### Post by yancek on 2015-04-19
On my Ubuntu 14.04 the folders/files in /boot/grub are:

fonts             grub.cfg   grubenv  locale gfxblacklist.txt   i386-pc  unicode.pf2


The i386-pc folder contains quite a large number of files, most with a .mod extension.  While booted to your other Ubuntu, create a mount point for sda7 with:  sudo mkdir /mnt/sda7
Then mount it to take a look at the grub directory:  sudo mount -t ext4 /dev/sda7 /mnt/sda7

If you don't have these files there, it won't boot.  Not sure what happened to that partition so it's difficult to suggest anything.  One thing you might try to get more information is to download the boot repair script and just select the option to Create a BootInfo Summary and post that file or a link to it so we have a better idea of what is happening.

---

### Post by AnyMation on 2015-04-20
Thanks yancek.

I mounted sda7. I can see all the files you mention in  /mnt/sda7/boot/grub. BTW, I'm not sure whether it is a circular  reference, but inside /mnt/sda7 I see *another* /mnt/sda7.

I remember running the Boot Info script in February, but I have today's fresh results. [Edit: See next post for the full file] 

Specifically: I noticed the[COLOR=#0000ff] "Unknown MBRs/Boot Sectors/etc" right at the end[/COLOR] - if that helps.

Thanks

---

### Post by AnyMation on 2015-04-20
Sorry, I should have thought about it. Attached is the full, smaller ZIPped file.

Thanks

---

### Post by oldfred on 2015-04-20
Easier just to post the link to the on-line copy of your Summary report.

You have several installs in sda and it looks like you ran Boot-Repair's autofix. That just installs the same copy of grub to every MBR. Better to use advanced mode and only have the one copy you want in the MBR of that drive. Also then better to have each install on a different drive with its boot loader in that same drive.

If you go into Boot-Repair's advanced mode you can choose an install and then which drive's MBR to install into.

You also have a problem with sdb1. You never ever install grub to a NTFS partition and almost never to a partition, just the MBR or boot sector of the drive. Windows has essential boot info in its NTFS partitions, even if just a data partition. And it must have info on start & size that matches partition table. With grub in the sdb1 partition boot sector, it may be valid, but not for NTFS. So use testdisk and see if you can restore the backup.

Testdisk is in repository so you can easily add it.
       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[URL="http://www.cgsecurity.org/wiki/Menu_Analyse"]http://www.cgsecurity.org/wiki/Menu_Analyse

[/URL]
 As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the boot sector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)


Are you using Windows? 
If not best not to have an NTFS partition. It needs chkdsk periodically and you can only run that from Windows or a Windows repair/recovery disk.

---

### Post by AnyMation on 2015-04-21
oldfred, thanks for the input.

Before I follow the steps you provided, and to help me better understand the context, some feedback and questions (which will show just how much of a noob I am in Ubuntu!).


[LIST]
[*]I noticed that grub seems to be installed on all the drives. It seemed odd to me but I thought that is the way it is done.
[*]No, I don't use Windows. I think the NTFS formatting is due to the disk previously being used in an older PC that had Windows on it.
[*]Having said that: does that make a difference to the points you made?
[*]Please help me understand how the points on NTFS drive relate to the problems I have with my Ubuntu install on sda7?
[*]When you say "So use testdisk and see if you can restore the backup": do you mean the backup of missing Ubuntu on sda7, or are you referring to a problem related to grub on NTFS?
[/LIST]

Thanks in advance.

---

### Post by oldfred on 2015-04-21
Grub only needs to be in the MBR of the drive you specify as boot drive in BIOS.
But I guess some users do not know what drive is default in BIOS, do Boot-Repair just adds it everywhere to be sure.

The testdisk restore of the backup boot sector for the NTFS partition. Not sure if Linux cares, but with grub in the boot sector Windows sees it as RAW or unformatted.
You need a Windows repair disk if you are keeping NTFS. It does need chkdsk periodically. Ubuntu runs fsck on every 40 or 60 reboots, but cannot run chkdsk on NTFS formats.

Both of above not related to grub reinstall but other issues noted in report.

You should run Boot-Repair's advanced mode, choose which install (partition) and then which drive you want to boot from in BIOS and install that version's grub to that drive's MBR.

---

### Post by AnyMation on 2015-04-22
Hi oldfred,

Although the NTFS drive is bootable, I do not use use it to boot from, but as a storage disk. This is achieved by the HD slot I plug it into the motherboard.

The drive I do boot from is of LInux partition type: Ext4.

I suppose I do have to look into that at some stage, but the NTFS drive is not giving me hassles at the moment (unless I just don't know it because I am ignorant?). Are you saying that I may be compromising the integrity of the disk (even though I only use it as a storage disk) by the fact that it is formatted as NTFS? It's not that I don't value your input, but the PC does not try to boot from sdb1.

The larger current problem I sit with, is not being able to boot into sda7.... what can I do about that?

Boot disk, with sda7:
[ATTACH=CONFIG]261478[/ATTACH]  with detail: [ATTACH=CONFIG]261480[/ATTACH]

Storage disk (bootable, but not booting from it):
[ATTACH=CONFIG]261479[/ATTACH]

Thanks.

---

### Post by oldfred on 2015-04-22
Boot flags are not used by grub2.
So that a partition has a boot flag does not mean anything. 
But a few BIOS require a boot flag to let any system boot, so we still suggest one. It is Windows that has to have a boot flag.

Did you run Boot-Repair's advanced mode and install grub using sda7 install to MBR of drive that is sda?

---

