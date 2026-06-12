---
title: "Grub boot problem:  file '/boot/grub/x86_64-efi/normal.mod' not found"
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by dshgna on 2014-10-13
Hi!

After running boot repair to fix a boot problem, I get a message that there was an error during boot repair. When I reboot I get the following error message:
error: file '/boot/grub/x86_64-efi/normal.mod' not found..

The log is as follows
[http://paste.ubuntu.com/8552716/](http://paste.ubuntu.com/8552716/)
My problem is that the log states that there is a problem in reading input/output from sda.

Any pointers to fix this issue is greatly appreciated!

Thanks!

---

### Post by yancek on 2014-10-13
It's a little strange that you have your EFI partitiion on sda11 which is near the end of the drive.  It also shows as a Recovery partition, not sure if that is standard.  Did you install windows 8 yourself or was it pre-installed?  You have both Ubuntu and windows efi files on that partition but you also have a separate BIOS boot partittion which is at the end of the drive.  You need to do either EFI/GPT or MBR/BIOS.  They don't mix.  That's about the extent of my knowledge so either do some googling or wait for someone more familiar with it to post.

---

### Post by dshgna on 2014-10-14
Windows 8 was pre-installed. I dual booted with Ubuntu which worked pretty ok till I had a power shortage at startup and then would not boot. But my Windows partition was accessible. 

I was prompted to create the BIOS partition by Boot recovery. Now Windows isnt accessible either. So should I go on and remove the BIOS partition. I did do some Googling but I am nervous to proceed as I am very much of a newbie when it comes to these stuff.

---

### Post by dshgna on 2014-10-14
This is what I've been trying so far.

1. Going by this [link]("http://ubuntuforums.org/showthread.php?t=2192777") I tried to see if I could boot the system. 

```

set root=(hd0,gpt12)
set prefix=(hd0,gpt12)/boot/grub
insmod linux
linux /vmlinuz root=/dev/sda12 ro
initrd /initrd.img
```

And I get an error saying
error: no such partition
However a ls on (hd0,gpt12) clearly shows the initrd.img file. So I am stuck.

2. I tried booting in legacy/uefi mode. Now the grub menu loads. BUT I cannot boot the Ubuntu system. It gives a buffer error And when I turn back to UEFI mode and try to load the live CD I cannot do it either as the error file '/boot/grub/x86_64-efi/normal.mod' not found shows up in UEFI mode too!

---

### Post by oldfred on 2014-10-14
Normal not found is often mixed BIOS and UEFI versions of grub. So you may be trying to use the grub in the protective MBR to boot (which is BIOS boot), but you actual install is for UEFI boot.

You show efi partition as sda2, but Boot-Repair showed errors in mounting that. And vendors add efi files in a recovery partition for hidden boot, which is what I think is your sda11.

I am not sure if one of these is better than the other?

Must be unmounted when you run this:
 sudo fsck -t vfat /dev/sda2

 sudo dosfsck -t -a -w /dev/sda2

Did you have a backup of your efi partition?

---

### Post by dshgna on 2014-10-15
Thanks a lot oldfred for your advice. I tried the commands out on my livecd which is thankfully booting now.

```

ubuntu@ubuntu:~$ sudo fsck -t vfat /dev/sda2
fsck from util-linux 2.20.1
fsck.fat 3.0.26 (2014-03-07)
Read 512 bytes at 0:Input/output error

ubuntu@ubuntu:~$ sudo dosfsck -t -a -w /dev/sda2
fsck.fat 3.0.26 (2014-03-07)
Read 512 bytes at 0:Input/output error

```

What can I do now? I have not created a backup EFI partition.

After some Googling I found that the IO error could be due to a disk failure! And my laptop is less than two years old!

---

### Post by oldfred on 2014-10-15
You should be backing up everything in system. Hard drives do fail, users make mistakes and data just seems to disappear. (Its the same thief that steals just one sock from the washing machine.)

You can check status of hard drive with Disks or Disk Utility (name changed in Ubuntu versions).
With disks you have to use icon in upper right for more actions and look at smart drive status. It can run lots of tests, but all I know is ok or not. Not ok is a new drive, but either way good backups still required.

I would backup efi partition and all of Windows. With Windows you just about need the image backup. With Ubuntu I prefer just to backup /home, and list of installed apps. I can just reinstall very quickly and reapply apps and /home. But I have high speed Internet to download new apps easily.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

From Linux you often cannot fix Windows issues, so you also need a Windows repair flash drive or CD.
      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

What I backup in Ubuntu:
      
 Oldfred's list of stuff to backup May 2011 (still current):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
I copy anything in /etc that I manually edit into /home so I do not normally backup /etc.
      
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by dshgna on 2014-10-15
Thank you again oldfred!

Result of running Smart tools:

[ATTACH=CONFIG]257241[/ATTACH]

Will get started creating a recovery image! Phew! Also just wondering:does having the dual boot result in premature HDD failures due to excessive reads?

Should I replace the HDD immediately or is it possible to keep using? Anyway to fix the boot issue?

Here-s the result I got from running badblocks. sda2(EFI), sda4(Windows 8), are the affected partitions. Also attached the gparted output of my partitions for further reference.

```

ubuntu@ubuntu:~$ sudo badblocks -n /dev/sda2
0
1
2
3
ubuntu@ubuntu:~$ sudo badblocks -n /dev/sda4
20457452
20457453
20457454
20457455
20464412
20464413
20464414
20464415
33757456
33757457
33757458
33757459
33757908
33757909
33757910
33757911
33761548
33761549
33761550
33761551
43708000
43708001
43708002
43708003
61264256
61264257
61264258
61264259
61415368
61415369
61415370
61415371
61557664
61557665
61590432
61590433
61590434
61590435
61759660
61759661
61759662

```

[ATTACH=CONFIG]257242[/ATTACH]

---

### Post by oldfred on 2014-10-15
Dual booting should not make any difference to drive's useful life. 
Something like efi partition would normally be reads only, very few writes.

You attached thumbnails not screen shots, too small to read. 
You can attach screen shot with the advanced editor and use the paperclip icon.

I thought the dosfsck would fix the efi partition, perhaps chkdsk from Windows works better?

       You do need to run chkdsk from a Windows repairCD or flash drive on your NTFS partitions. You cannot run chkdsk from Linux repair tools.

I have seen some post that Smart Tools may give errors and drive can be used, but I do not think I would trust any drive that it says has issues. It would of course fail completely just before you were planning on next backup.

---

### Post by dshgna on 2014-10-15
Edited above post to add images.

Is it possible to create a new EFI partition without recovering the old one? Also is it ok to go on and delete the BIOS partition I created?

---

### Post by oldfred on 2014-10-15
If you are booting with UEFI, you do not need the bios_grub partition. But it is only 10MB, normally it only needs to be 1 or 2MB.

You need to run chkdsk from Windows, on NTFS partition.

You can create a new efi partition for Ubuntu easily with a reinstall of grub, but Windows does not have all the files. I think running Windows repairs from a repair flash drive also will recreate efi files, but have never run it.  
Efi partition is not large and can easily just be copied to a flash drive.

You can only have one efi partition per hard drive. With gparted it is the boot flag that determines the efi partition. Actually the efi partition is set by having a very long GUID, and differnent tools use different ways of assigning the GUID to the partition. If you use gdisk it is ef00 for the ESP(efi) partition an ef02 for the bios_grub partition.

```
Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 250069680 sectors, 119.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): F7EC3F54-45C1-4D9B-BEF0-FC0938932851
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 250069646
Partitions will be aligned on 2048-sector boundaries
Total free space is 193936762 sectors (92.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1026047   500.0 MiB   EF00  efi
   2         1026048         1030143   2.0 MiB     EF02  
   3         1030144        52229362   24.4 GiB    8300  trusty
   4       246163456       250068991   1.9 GiB     8200  

```

---

### Post by dshgna on 2014-10-17
> **oldfred said:**
> 
From Linux you often cannot fix Windows issues, so you also need a Windows repair flash drive or CD.
      
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)


Unfortunately, all these options require being able to boot into the existing Windows system, which I cannot do. What other options do I have?

---

### Post by oldfred on 2014-10-17
If you know someone at school, work or wherever, you can make a repair flash drive from their install. Just need to be 64 bit which most are.

       We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $20 or $40  for the download. So make one yourself before you have to pay to get one.
[http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/](http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/)

If just minor repairs, some of the free third party repair tools may work. They usually have a limited free version and then more complete versions that cost.

      
 EASEUS Partition Master - Windows .exe
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard -  boot CD or flash also, chkdsk & other Windows repairs
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

   Third party chkdsk tools
Hiren's Boot CD, and do a chkdsk on the XP
[http://www.hirensbootcd.org/](http://www.hirensbootcd.org/)

---

