---
title: "Hard disk failure in multiple boot system, how to remove non-existing systems"
date: 2013-12-17
forum: Installation &amp; Upgrades
---

### Post by zuheyr2 on 2013-12-17
Hello,

One of my 2 hard disks died, taking with it the Windows operating system as well as some older Ubuntu versions. 
I am using Grub to boot Ubuntu 12.04 and what used to be several windows distros are still in the boot menu. 

I am happy this will be Christmas cleaning but how do I clean the grub menu? Installing Windows on a new hard disk
will automatically correct the menu? Because Grub asks me to manually skip mounting disks that are not mountable...

I would like to try the latest Ubuntu distro as well on the new hard disk.

Thanks for reading!
Happy holidays and best wishes, 
Zuheyr

---

### Post by fantab on 2013-12-17
Where is your grub installed? on the good HDD or dead HDD?

If its on the good HDD then remove the dead HDD and run:
```
sudo update-grub
``` 
after booting into ubuntu 12.04, that should clear up the Grub menu.

---

### Post by zuheyr2 on 2013-12-17
Thank you! 

Sorry, silly of me, thanks to Heavens, I am saved, the grub is installed on the good disk and 
it boots.  Thank you!

---

### Post by zuheyr2 on 2013-12-25
Hello,

I closed the thread as solved thinking it would be when I throw away the bad disk and update grub
but it did not solve the problem. I even installed a parallel windows and grub found my old windows with it 
and I installed also another 12.04 additional one whiel playing with Live CD.
 
However, I still get that cannot mount the disk, waitm, enter S to skip, M for manual configuration message...

Happy holidays, thanks very much for reading!

Zuheyr

---

### Post by fantab on 2013-12-25
Download and Run the **[BootInfo Script]("http://bootinfoscript.sourceforge.net/")**. Use [this]("http://paste.ubuntu.com/") to copy-paste the contents of your 'Results.txt file here as a link.

---

### Post by grahammechanical on 2013-12-25
When we run update-grub the command runs a Grub utility called os-prober. It is os-prober that searches for other operating systems and if it finds them it includes them in the configuration files that Grub uses to produce that menu. This is why it is recommended that the faulty disk with those versions of Windows and Ubuntu on it be disconnected. Then os-prober will not probe that hard disk. There is another command that you can run after running update-grub

```
sudo grub-install /dev/sda
```

I find that sometimes we need this command to make the changes in the Grub configuration files active. In other words, change the Grub menu.

That command will work if there is only one hard disk in the machine. If there is a second hard disk then you may need to change /dev/sda to /dev/sdb if you are running the command from Ubuntu on the second hard disk (sdb) and not the first hard disk (sda).

Regards.

---

### Post by zuheyr2 on 2013-12-25
Hello,

Much appreciated, thank you.

Here is the link:
[http://paste.ubuntu.com/6635604/](http://paste.ubuntu.com/6635604/)

It is a bit long I am afraid. Thank you very much. Regards, Zuheyr

---

### Post by zuheyr2 on 2013-12-25
Thank you for the response. 

I have replaced the faulty disk which turned out to be the first hard disk, so Ubuntu 12.04 happened to be 
on the /dev/sdb. Mainly I left it to boot-repair recommended corrections but I have also tried other solutions including
advanced options with purging the grub and then creating a new one with the chroot etc... 


At this moment in time when I have created the bootinfo script results above, there is another 12.04 in sda that the grub does not detect.

Thank you very much for your time! Regards, Zuheyr

---

### Post by oldfred on 2013-12-25
Your sda is now a 3TB drive with gpt partitioning. Windows will only boot from gpt partitioned drives with UEFI, but you show a standard BIOS type install (labelled 1TB, which probably was MBR)? Also the Windows in sdb3 has no boot files. Typically Windows installs all boot files to the BIOS boot drive and partition with the boot flag. So unless sda is BIOS and has a working Windows you cannot boot sdb3. But since a primary partition you may be able to copy boot files to sdb2 and use a Windows repairCD or flash drive to make it work.

You have installed grub2's boot loader to many partitions. That does not work normally and should only be done if you only have no other way to boot. With several hard drives you can install grub to any drive for any install. Best to have grub installed to same drive as your install so when drive fails you can still boot another drive.
If installing grub to a gpt partitioned drive you need to create a tiny 1 or 2MB unformatted partition with gparted and right click manage flags to add the bios_grub flag. It can be anywhere on drive.

But with new gpt partitioned drives I also suggest a 300 to 400MB fat32 partition at the start. When drive is then converted to UEFI boot on a new system you do not have to totally reformat to add the efi partition.

You may want to houseclean some old kernels. I like to use synaptic.
       Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

If your boot install has any partitions from sda and sda is not working then you will get error messages on those partitions not being mounted. Or if a new drive with new UUIDs then you need to update UUIDs. I did not attempt to compare them all. :)

---

### Post by fantab on 2013-12-25
How did you determine that one of your HDD is faulty? I hope you are absolutely sure that your HDD is at fault.
Boot-Repair utility creates a LINK to 'Bootinfo Summary', you must post that link here as well; so we know what boot-repair found and how it repaired the boot or what it recommends.

Boot with the Live DVD/USb and post the output of:
```
sudo parted -l
sudo fdisk -l
sudo blkid
```

Like oldfred points out, you have some house-cleaning to do as you have accumulated some old and unused kernels. We can do this later. Lets just get your system booting again.
(If you can then please don't make any changes to HDD's between you posting the outputs and us replying).

---

### Post by zuheyr2 on 2013-12-26
Oldfred, I am very grateful, thank you for this thorough answer. Your reply showed me there are so many things I overlooked, in my previous search. 

[B][COLOR=#000000]> Windows will only boot from gpt partitioned drives with UEFI, but you show a standard BIOS type install (labelled 1TB, which probably was MBR)?[/COLOR]
[/B]
I confess only now I your reference link to find what is UEFI and all my Ubuntu research about how to add windows after ubuntu just mentioned make a partition and put the windows there...
Forgive my ignorance, sincerely.

[FONT=arial black][COLOR=#000000]**>So unless sda is BIOS and has a working Windows you cannot boot sdb3.**
[FONT=arial][/FONT]
[FONT=arial]Yes that's why I needed to install another Windows 7 that can load my previous Windows 7 which was no longer available. 
[FONT=arial black]
[/FONT][/FONT][/COLOR][U][B][COLOR=#000000]>But since a primary partition you may be able to copy boot files to sdb2 and use a Windows repairCD or flash drive to make it work.
[/COLOR][/B][/U][COLOR=#000000][FONT=arial][FONT=arial black][FONT=arial]
I am not sure I grasp this, which files exactly I should copy. I must look at this more. [/FONT]

** >**[/FONT][/FONT][/COLOR][B][COLOR=#000000]That does not work normally and should only be done if you only have no other way to boot. 
[/COLOR][/B][FONT=arial][COLOR=#000000]
"recommended" Boot-repair help was not working, that's how I managed to make it boot, using the advanced options of the boot-repair.
[/COLOR][/FONT][B][COLOR=#000000]
[FONT=arial][/FONT]>But with new gpt partitioned drives I also suggest a 300 to 400MB fat32 partition at the start. When drive is then converted to UEFI boot on a new system you do not have to totally reformat to add the efi partition.[/COLOR][/B]
[FONT=arial]I can still scrap the hard disk /dev/sda and do what you suggest but for /dev/sdb probably it is too late!? I am not touching anything, not cleaning yet atm as fantab asked me not to until we sort out the situation.

Great many thanks indeed. Kind regards, Zuheyr

[/FONT][/FONT]

---

### Post by zuheyr2 on 2013-12-26
Fantab, my sincere thanks, much appreciated.

[FONT=arial black][COLOR=#000000]> How did you determine that one of your HDD is faulty? I hope you are absolutely sure that your HDD is at fault.[/COLOR]
[/FONT]
Grub would no longer find my Windows on it, it was saying no operating system is found. I am not absolutely sure, no. No I did not check the disk 
to see if it is faulty. My desktop is pretty old, and I already changed several hard disks (after checking to see they are faulty)...

But if the MBR was on the /dev/sda as OldFred mentions, how the system could reboot without /dev/sda then?? I am in a rush for my projects so I did not think enough perhaps.

The system reboots but the problem is this:
I get the error from grub: UUID=0c29c6c5-9817-4d4f-a51c-2f736bb61c2b is not yet ready or not present. 
It asks me to wait, or type S to skip (which I do) or type M for manual modification. 


I thank you very much, most kind of you, before including the long ouputs to the commands you asked me to provide you with.
Kind regards, zuheyr 
[FONT=arial black]**The output of "sudo parted -l"**[/FONT]
Model: ATA WDC WD30EFRX-68E (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1049GB  1049GB  primary   ntfs            boot
 2      1049GB  1592GB  544GB   extended
 5      1049GB  1049GB  599MB   logical   ext4
 6      1049GB  1079GB  30.0GB  logical   ext4
 7      1079GB  1092GB  13.0GB  logical   linux-swap(v1)
 8      1092GB  1592GB  500GB   logical   ext4




Model: ATA WDC WD20EARX-00P (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  322GB   322GB   primary   ntfs
 3      322GB   913GB   591GB   primary   ntfs            boot
 4      913GB   1314GB  401GB   extended                  lba
 5      913GB   913GB   537MB   logical   ext4
 6      913GB   935GB   21.5GB  logical   ext4
 7      935GB   948GB   12.9GB  logical   linux-swap(v1)
 8      948GB   1314GB  366GB   logical   ext4
 2      1314GB  2000GB  687GB   primary   ntfs
========================================

[FONT=arial black]**Output of sudo fdisk -l:**[/FONT]
Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004f7ff


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  2048002047  1024000000    7  HPFS/NTFS/exFAT
/dev/sda2      2048004094  3109720063   530857985    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      2048004096  2049174017      584961   83  Linux
/dev/sda6      2049175552  2107767348    29295898+  83  Linux
/dev/sda7      2107768832  2133157887    12694528   82  Linux swap / Solaris
/dev/sda8      2133159936  3109720063   488280064   83  Linux


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x506f0275


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   629139455   314568704    7  HPFS/NTFS/exFAT
/dev/sdb2      2565875712  3907028991   670576640    7  HPFS/NTFS/exFAT
/dev/sdb3   *   629139456  1782573055   576716800    7  HPFS/NTFS/exFAT
/dev/sdb4      1782575041  2565875711   391650335+   f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sdb5      1782575104  1783623679      524288   83  Linux
/dev/sdb6      1783625728  1825568767    20971520   83  Linux
/dev/sdb7      1825570816  1850736639    12582912   82  Linux swap / Solaris
/dev/sdb8      1850738688  2565875711   357568512   83  Linux


Partition table entries are not in disk order
=================================

[FONT=arial black]**output of sudo blkid:**[/FONT]
/dev/sda1: LABEL="WD1TB" UUID="6F16032E3A5685E2" TYPE="ntfs" 
/dev/sda5: UUID="6e9647fd-9722-4117-999e-8bd692cb8ddd" TYPE="ext4" 
/dev/sda6: UUID="f01d10c3-f751-4c7c-8f77-df81cac0320a" TYPE="ext4" 
/dev/sda7: UUID="2c5e0156-6f29-4839-b1f8-583cfb515a05" TYPE="swap" 
/dev/sda8: UUID="beb528f4-523e-4a30-a700-c0e16fe20cbd" TYPE="ext4" 
/dev/sdb1: LABEL="storage" UUID="5A3E999B3E9970AD" TYPE="ntfs" 
/dev/sdb2: LABEL="new" UUID="3608CDAC3F6806E5" TYPE="ntfs" 
/dev/sdb3: UUID="01CD643B0CEAE0A0" TYPE="ntfs" 
/dev/sdb5: UUID="3c7a72cc-b856-4d82-9121-4b968540299a" TYPE="ext4" 
/dev/sdb6: UUID="dbf12d4e-838e-4117-a486-9034b9ff7957" TYPE="ext4" 
/dev/sdb7: UUID="8de601aa-e3bb-4131-8b61-928a0f76cfb0" TYPE="swap" 
/dev/sdb8: UUID="cc5e88b9-c95f-45a0-a7e7-ed14172aebeb" TYPE="ext4" 
================================================

---

### Post by fantab on 2013-12-26
> I get the error from grub: UUID=0c29c6c5-9817-4d4f-a51c-2f736bb61c2b is not yet ready or not present. 
It generally means: 
1. That there could be filesystem errors on the HDD or partition. Running 'CHKDSK' from Windows will resolve this.
---OR---
2. That the UUID of your partition changed somehow. Replacing the old UUID of the partition with the new in /etc/fstab or Grub files will also resolve the issue.

If you look at the UUIDs from the 'blkid' output you will see that there is no UUID=0c29c6c5-9817-4d4f-a51c-2f736bb61c2b, for which you are getting errors. 

I don't see that 1Tb HDD in your output. It would have helped if we could see the UUIDS of that disk as well.

Most importantly, HDD larger than 2TB are not supported by 'msdos'/MBR partition table. You should use [GUID Partition Table [GPT]]("https://wiki.archlinux.org/index.php/GPT"). Windows will only boot from GPT in UEFI mode.
```
Model: ATA WDC WD30EFRX-68E (scsi)
Disk** /dev/sda**: 3001GB
Sector size (logical/physical): 512B/4096B
**Partition Table: msdos**
```

This disk surely would have had GPT originally. You, most likely, changed it to 'msdos'/MBR.
You will have to create a new GPT table. This will erase all the data and partitions on the HDD. You need to BACKUP your data.

I would go a step further and also make the other 2Tb HDD GPT, as well.
But before that you have to make sure your computer is equpped with UEFI. If it does have UEFI then you need to reinstall all your OS in UEFI.
If you don't have UEFI then keep your second HDD as 'msdos' and boot all your OS from it.

Run SMART tests on the 1Tb HDD to find out if it is indeed faulty. You can run the tests with the utility 'Disks' from Live Ubuntu after re-plugging the faulty HDD.

---

### Post by zuheyr2 on 2013-12-26
Thank you! 

I will definitely run the CHKDSK on the old 1TB disk, as well as the SMART tests. In my previous disk failures Ubuntu always issued  warnings, not this time.  

Yes I have taken that 1TB disk (as I only have two hard disk bays in my Dell Inspiron 530S slim tower) but I will put it back, check its UUID and test it.

I only provided the Windows with a NTFS partition in /dev/sda as per  my incomplete Ubuntu research. Perhaps I created the mess by asking the boot-repair
to put grub2 loaders in many partitions. 

The second thing to do is to check if my computer, Dell Inspiron 530s Slim tower, is equipped with UEFI. 

Thank you very much. I do hope this thread will be useful to many multiple booters.
 
Kind regards, Zuheyr

---

### Post by oldfred on 2013-12-26
You can boot Ubuntu from gpt partitioned drives with BIOS. That is all I have and use gpt on two of my drives and even one flash drive has gpt.
But Windows only boots from gpt with UEFI. 

If system is older, then it is unlikely to have UEFI. Systems started to have UEFI/BIOS with Intel second gen chips. Only some later Windows 7 systems boot with UEFI.

If you convert your 3TB drive to MBR(msdos) you also then convert it to a 2TiB drive as that is the max for MBR since MBR is about 30 years old and TB was not even thought about on a PC back then.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by zuheyr2 on 2013-12-26
Hello,

Most sincere thanks. I think I have enough information to do my late homework and put the pieces together. 

I will not yet close the thread until I solve get a perfect boot as I hope this thread may be helpful 
to fellow Ubuntu beginners.

Best wishes and best regards.

---

