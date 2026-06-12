---
title: "Installing on a large hard drive"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by jis4joe on 2011-09-27
[FONT=Arial]I'm trying to install Ubuntu onto a 2TB HDD. I've tried USB and CD installations of both 10.10 and 11.04. No combination works. The installation appears to complete but when I try to boot the system I get the following error:[/FONT]
**[SIZE=3]"no bootable device insert boot disk and press any key"[/SIZE]**
After trying USB and CD installs of both 10.10 and 11.04 and much searching for a solution I stumbled over:
 
[http://www.linuxquestions.org/questions/debian-26/unable-to-boot-fresh-install-on-2tb-harddrive-debian-ubuntu-838681/](http://www.linuxquestions.org/questions/debian-26/unable-to-boot-fresh-install-on-2tb-harddrive-debian-ubuntu-838681/)
 
which describes my symptoms exactly but I haven't been able to replicate the results. Looking for some magic from these forums.
 
Can anyone point me to a forum thread that desicribes a definitive solution / how-to guide for doing this? I can't be the only one that has run into this problem.
 
Thanks,
 
Joe

---

### Post by YesWeCan on 2011-09-27
Would you post the output of
[COLOR="DarkSlateBlue"]sudo sfdisk -luS[/COLOR]

---

### Post by lightwarrior on 2011-09-27
The link you supplied has the answer:  You need to create a separate /boot partition.

" I have solved the problem by creating the following partitions:

1. /boot <- Boot flag "ON"
2. / <- Boot flag "OFF" (Main harddrive)
3. swap <- Boot flag "OFF"

By creating the /boot partition and booting into that one before any other partition fixed the problem 

Thanks for your help everybody!
Last edited by Hypertenzion; 10-18-2010 at 02:12 PM."

---

### Post by jis4joe on 2011-09-27
further down in the link I provided there is other information:
 
* primary 100MB /boot 
* primary 4GB swap
* primare 15GB / [boot flag]
* logical {a lot of partitions}
 
which is correct?  I have tried both with no luck.
 
I will try to post output of
 
[COLOR=#483d8b]sudo sfdisk -luS[/COLOR] 
 
Will need to boot from USB in order to do this ie... obviously can't boot from hard drive.

---

### Post by jis4joe on 2011-09-28
Thanks for your help.  Here is the output you've asked for:
 
[EMAIL="ubuntu@ubuntu:/$"]ubuntu@ubuntu:/$[/EMAIL] sudo sfdisk -luS
 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 243201 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0
 
   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             1 3907029167 3907029167  ee  GPT
  start: (c,h,s) expected (0,0,2) found (0,0,1)
/dev/sda2             0         -          0   0  Empty
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
 
Disk /dev/sdb: 1022 cylinders, 248 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/256/60 (instead of 1022/248/62).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0
 
   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        32  15728639   15728608   b  W95 FAT32
  start: (c,h,s) expected (0,0,33) found (0,1,1)
  end: (c,h,s) expected (1023,255,60) found (975,255,60)
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty
[EMAIL="ubuntu@ubuntu:/$"]ubuntu@ubuntu:/$[/EMAIL]

---

### Post by YesWeCan on 2011-09-28
One problem is that you've got a GPT (GUID partition table) on your 2TB disk. This is not necessary.

Note that the latest Ubuntu installer has a dyfunction, in my opinion, because if you tell it to use an entire, blank disk of 2TB it will format it with GPT. It should not do this because the MBR size limit is 2TiB (2.2TB) not 2TB.

I recommend erasing the drive's GPT header and reformating with an MBR and starting again.
```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=2
```
Then use Disk Utility to "format drive" and choose MBR (master boot record) then try installing Ubuntu again.


The only reason you might need a separate boot partition at the start of the drive is if you have a type of BIOS, usually an old BIOS, that does not allow Grub to access partitions more than 137GB into the drive and you are trying to boot a Ubuntu root partition whose boot files are located beyond 137GB. I think you can reboot and look in the BIOS to see whether it shows your drive as 2TB or 137GB. I think this is unlikely to be a problem in your case.

---

### Post by jis4joe on 2011-09-28
Thank you YesWeCan.  I've followed your directions and believe I'm back to a completely blank drive ie...

ubuntu@ubuntu:/$ sudo sfdisk -luS

Disk /dev/sda: 243201 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             0         -          0   0  Empty
/dev/sda2             0         -          0   0  Empty
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

Can you elaborate on "starting again"?  I've tried so many things that haven't worked I don't know which one should have worked.  I know that I never saw anything that resembled an option to choose primary/logical when attempting the advanced partition option from the installer.

---

### Post by YesWeCan on 2011-09-28
> **jis4joe said:**
> Can you elaborate on "starting again"?  I've tried so many things that haven't worked I don't know which one should have worked.  I know that I never saw anything that resembled an option to choose primary/logical when attempting the advanced partition option from the installer.

Sure. Well, I think you are in a position to install Ubuntu now. I am not sure exactly what you want to do?

You should be able to just run the installer and choose "entire disk" and let it do its thing. If you want to define your own partitions, either primary or logical, you'll need to choose "something else".

---

### Post by jis4joe on 2011-09-28
OK.  I tried the UBUNTU installer again, let it do "entire disk", and had same results.  Rebooted with USB drive.  Here is output:

ubuntu@ubuntu:/$ sudo sfdisk -luS

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 243201 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             1 3907029167 3907029167  ee  GPT
		start: (c,h,s) expected (0,0,2) found (0,0,1)
/dev/sda2             0         -          0   0  Empty
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

What I want to do is:

Have UBUNTU installed on ~ 50k partition, have the rest of the 2TB available for network sharing with other Windows PCs, Ubuntu PCs, Android Smart Phones, iPods, etc... around the house (I have five kids).

Thanks again for your help YesWeCan.

---

### Post by srs5694 on 2011-09-28
> **YesWeCan said:**
> One problem is that you've got a GPT (GUID partition table) on your 2TB disk. This is not necessary.

It's not necessary, but for a Linux-only installation it is, IMHO, preferable. GPT has several advantages over the older MBR system, including:


[list]
[*]Support for over-2 TiB disks, which is not an issue for jis4joe's 2 TB (~1.8 TiB) disk.
[*]No distinction between primary, extended, and logical partitions. These distinctions have been a thorn in the side of PC users for decades, and with GPT they disappear.
[*]CRCs of important GPT data structures are stored on the disk, making detection of corrupted data structures easier.
[*]A backup of the main GPT data structures is stored at the end of the disk, making recovery from some types of accidents easier.
[*]Partitions have labels. These are sometimes redundant with filesystem labels, but depending on the partitioning tools you use, they can be useful in identifying the purpose of a partition.
[*]No linked-list data structures. MBR uses these for its logical partitions, and they can get tangled up and damaged in peculiar ways.
[/list]


There is one big drawback to GPT: Windows will boot from a GPT disk only if the computer uses UEFI firmware. If you've got the more common BIOS firmware, Windows will boot only from MBR disks. GPT also requires a slightly different knowledge base, and there are sometimes GPT-specific partitioning requirements. Most notably, if you install Ubuntu on a GPT disk, it's highly desirable to create a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) on the disk for GRUB 2 to use. You can do this in GParted or parted by setting the "bios_boot flag" on the partition, or in GPT fdisk (gdisk, cgdisk, or sgdisk) by setting a partition type code of EF02. The BIOS Boot Partition can be tiny -- as small as about 32 KiB, although 1 MiB is a more common size.

It's possible that the error message jis4joe encountered was due to a buggy BIOS that insists on seeing a boot flag set on an MBR partition. If so, this problem can easily be overcome by using Linux fdisk (*not* parted, GParted, or any other libparted-based tool) to set the MBR boot/active flag on the 0xEE "protective partition" in the MBR of a GPT disk.

So to sum up, if you, jis4joe, are doing a Linux-only installation, I recommend you go back to GPT, create a BIOS Boot Partition, and install normally. The lack of a BIOS Boot Partition may be what caused your problem in the first place, although it's also possible it's the lack of a boot flag on the protective partition. This second possibility may make for very easy recovery from the damage you inflicted at YesWeCan's suggestion (see below).

> I recommend erasing the drive's GPT header and reformating with an MBR and starting again.
```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=2
```Then use Disk Utility to "format drive" and choose MBR (master boot record) then try installing Ubuntu again.

This instruction only deletes the GPT's main header. The backup header remains in place, and depending on what's done with the disk, it can cause the "resurrection" of the old partition table. If you've repartitioned the disk as an MBR disk, such data "resurrection" can cause you to lose your proper MBR table. I realize that you've already run this command, jis4joe, but there are several ways you can proceed that are safe:


[list]
[*]Create a fresh GPT on the disk and start from scratch.
[*]Use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) on the disk. It will detect the backup GPT data and give you the chance to restore it. You'll then have your old installation back and you can troubleshoot it or start from scratch, as you see fit.
[*]You can use parted or GParted to create a fresh MBR partition table. These programs delete the stray GPT data, thus making the disk safe to use as an MBR disk.
[*]You can use the "z" option on gdisk's experts' menu to completely destroy the GPT data, or the -Z option to sgdisk to do the same.
[*]If you've already created a new MBR on the disk using a tool that does not delete the stray GPT data (such as fdisk), you can run my [FixParts](http://www.rodsbooks.com/fixparts/) program on it. This will erase the stray GPT data. FixParts, however, refuses to run on a disk with nothing in the MBR, which is the state that the disk is in immediately after YesWeCan's dd command, so it's only an option if you've already used the disk in some other way.
[/list]


[quote=YesWeCan]You should be able to just run the installer and choose "entire disk"  and let it do its thing. If you want to define your own partitions,  either primary or logical, you'll need to choose "something else".[/quote]

As you pointed out in an earlier post, the Ubuntu installer defaults to GPT on 2 TB disks, so following these instructions with the disk in its current state will just end up back at the starting point.

Jis4joe, you have basically three options:


[list]
[*]Use gdisk to resurrect your last partitions and troubleshoot the installation.
[*]Create a fresh GPT on the disk, create a BIOS Boot Partition, and install normally.
[*]Completely wipe the GPT data, create an MBR partition table and manually partition, and install normally.
[/list]


The first option *might* make for very easy recovery, since if the boot problem was caused by the [buggy BIOS issue](http://www.rodsbooks.com/gdisk/bios.html) to which I referred earlier, once the system is recovered, you can use fdisk to set the active/boot flag on the 0xEE partition and your system will begin booting. If you decide to attempt recovery in this way, I recommend you use [Parted Magic](http://partedmagic.com/) to boot the system, since it comes with all the necessary tools. Once it's booted:


[list=1]
[*]Open a terminal window.
[*]Type "gdisk /dev/sda". It will ask you whether to use the damaged GPT or to create a new one. Type "1" ("use current GPT").
[*]Type "p" to review your partitions. Look for one with a type code of EF02. If such a partition doesn't exist, create it with the "n" command. If it does exist, don't create any new partitions.
[*]Type "w" to save your changes.
[*]Type "fdisk /dev/sda".
[*]Type "p" to review the MBR partition table. It should have just one entry, with "ee" under the "Id" column.
[*]Type "a" and enter "1" as the partition number. This toggles the boot/active flag, which should appear as an asterisk ("*") under the "Boot" column if you use "p" again.
[*]Reboot. If you're lucky, Ubuntu will boot normally. If not, you can either start again or re-install GRUB on your current system.
[/list]


Another option is to go with a fresh installation. I don't know quite what the Ubuntu installer does with most of its auto-partitioning options -- some of them might convert MBR to GPT, for instance. Thus, I recommend using the "something else" or "other" option (whatever it's called) to do the manual partitioning, *after* setting up the partitions manually using GParted or some other tool. If you go with GPT, be sure to include a BIOS Boot Partition. If you use GPT and create a BIOS Boot Partition but the system doesn't boot, try setting the boot/active flag, as just described.

---

### Post by srs5694 on 2011-09-28
> **jis4joe said:**
> OK.  I tried the UBUNTU installer again, let it do "entire disk", and had same results.  Rebooted with USB drive.  Here is output:

I'm afraid I began my last post before this one appeared, so some of what I posted is no longer relevant.

I recommend you use Linux's fdisk to set the boot/active flag on the 0xEE partition, as described in the procedure near the end of my original post. Follow steps 1 and 5-8; ignore the gdisk commands (unless you repeat the erasure of the primary GPT data). This will probably make your system bootable, but I can't guarantee that with 100% certainty. If it doesn't, you have two options:


[list]
[*]You can post further diagnostic information in the form of the RESULTS.txt file created by the [Boot Info Script.](http://sourceforge.net/projects/bootinfoscript/) If you post it, please do so as an attachment or between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility. This script's output may have clues to help diagnose the problem.
[*]You can *completely* wipe the GPT data (<snip>), manually create an MBR partition table, and re-install Ubuntu.
[/list]

---

### Post by jis4joe on 2011-09-28
IT BOOTED!  Here's what I had to do to get UBUNTU installed on a 2TB HDD:

1)  Install Ubuntu using the standard installer (CD or USB stick produce same results).
2)  Select "entire disk" when given the option.
3)  When complete try booting from 2TB HDD and get error:

"no bootable device insert boot disk and press any key".

4)  Reboot into Ubuntu from CD or USB stick.
5)  Open a terminal window.
6)  Type "sudo fdisk /dev/sda".
7)  Type "p" to review the MBR partition table. It should have just one entry, with "ee" under the "Id" column.
8 )  Type "a" and enter "1" as the partition number. This toggles the boot/active flag, which should appear as an asterisk ("*") under the "Boot" column if you use "p" again.
9)  IMPORTANT:  Type "w" to write changes to disk and exit.
10)  Reboot from HDD.

Thank you srs5694 and YesWeCan for your help.  There is absolutely no way I would have figured this out without your help.

My ultimate goal now that I have this working is to partition things on the drive such that the OS lives on a single small partition and all of my data is stored on a separate partition so that when I want to upgrade the OS (ie... with 11.10 next month) I don't loose all of the data stored therein.  Any suggestions on how to get started with that?  Is there a step-by-step process that walks through recommended "something else" during the installation for this kind of setup?  I think what I want is:

? how much need for BIOS boot?
~ 50G for OS
~ 4G for swap
Rest of HDD for data

Once these partitions are created will the installer know where to put what?  As you can tell... I'm a bit over my skis on most of this.

From srs5694 below:
"...using the "something else" or "other" option (whatever it's called) to do the manual partitioning, after setting up the partitions manually using GParted or some other tool. If you go with GPT, be sure to include a BIOS Boot Partition. If you use GPT and create a BIOS Boot Partition but the system doesn't boot, try setting the boot/active flag, as just described."

I understand only the last sentence of this because I just did it.  It is still not clear to me if what I did that finally worked is using GPT or MBR.

Thanks again for everyone's support.

---

### Post by srs5694 on 2011-09-28
> **jis4joe said:**
> IT BOOTED!

I'm glad to hear it!

> My ultimate goal now that I have this working is to partition things on the drive such that the OS lives on a single small partition and all of my data is stored on a separate partition so that when I want to upgrade the OS (ie... with 11.10 next month) I don't loose all of the data stored therein.  Any suggestions on how to get started with that?  Is there a step-by-step process that walks through recommended "something else" during the installation for this kind of setup?  I think what I want is:

? how much need for BIOS boot?
~ 50G for OS
~ 4G for swap
Rest of HDD for data

The BIOS Boot Partition can be tiny. 32 KiB is sufficient, but a more common choice is 1 MiB, just because of partition sizing and alignment policies in modern disk partitioning tools.

50 GiB is more than generous for an Ubuntu OS partition. A basic installation only takes about a tenth of that, and even if you install all the software imaginable, it's unlikely you'll push beyond about half that. You might consider setting aside a spare OS-installation partition for future use. That might be useful if you want to test a new version of Ubuntu, or even an entirely different distribution, without wiping out what you've got.

The usual "data" partition is /home, since your home directory is a subdirectory of that directory.

> From srs5694 below:
"...using the "something else" or "other" option (whatever it's called) to do the manual partitioning, after setting up the partitions manually using GParted or some other tool. If you go with GPT, be sure to include a BIOS Boot Partition. If you use GPT and create a BIOS Boot Partition but the system doesn't boot, try setting the boot/active flag, as just described."

I understand only the last sentence of this because I just did it.  It is still not clear to me if what I did that finally worked is using GPT or MBR.

From your description, you're using GPT. The GParted program is a common Linux partitioning program, and it enables you to create a BIOS Boot Partition by creating a partition and then setting its "bios_grub" flag. I'd gotten the impression that you'd set up manual partitions based on your earlier posts, but perhaps I misinterpreted those....

If you need more specific advice on your current setup, I suggest you open a Terminal window and type the following command:

```

sudo parted /dev/sda print

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. That will put what you post in a code block like I used just above. This has the effect of keeping the output of some text-mode commands, like the parted output, legible.

---

### Post by YesWeCan on 2011-09-28
> **srs5694 said:**
> [*]You can *completely* wipe the GPT data (<snip>), manually create an MBR partition table, and re-install Ubuntu.
[/list]

<snip>

---

### Post by YesWeCan on 2011-09-28
> **jis4joe said:**
> OK.  I tried the UBUNTU installer again, let it do "entire disk", and had same results.  Rebooted with USB drive.  Here is output:

ubuntu@ubuntu:/$ sudo sfdisk -luS

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 243201 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             1 3907029167 3907029167  ee  GPT
		start: (c,h,s) expected (0,0,2) found (0,0,1)
/dev/sda2             0         -          0   0  Empty
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

What I want to do is:

Have UBUNTU installed on ~ 50k partition, have the rest of the 2TB available for network sharing with other Windows PCs, Ubuntu PCs, Android Smart Phones, iPods, etc... around the house (I have five kids).

Thanks again for your help YesWeCan.

Sorry about that, even I (who am very cynical about the installer) didn't consider the possibility that it would reformat as GPT when a valid MBR existed! Worth knowing.

<snip> I would still advice you and anyone else reading this to use MBR and not GPT. There is no advantage to GPT (<snip>) and existing tools are fully tested with MBR but sometimes go wrong with GPT. GPT is more trouble than benefit unless you are forced to use it by having a disk >2TiB.

To install without the Ubuntu installer going awry I guess you'd have to select "special" and create the partitions manually. :)

---

### Post by YesWeCan on 2011-09-28
> **srs5694 said:**
> It's not necessary, but for a Linux-only installation it is, IMHO, preferable. GPT has several advantages over the older MBR system, including:
<snip>
> 
[list]
[*]Support for over-2 TiB disks, which is [COLOR="Red"]not an issue[/COLOR] for jis4joe's 2 TB (~1.8 TiB) disk.
[*]No distinction between primary, extended, and logical partitions. These distinctions have been a thorn in the side of PC users for decades, and with GPT they disappear.
<snip> The decades-tested MBR extended partitions are perfectly easy to use and properly supported by existing linux tools.
> [*]CRCs of important GPT data structures are stored on the disk, making detection of corrupted data structures easier.
CRCs needed to check the GPT tables themselves because they are so complicated. This is a non-advantage for the OP and also in practice.
> [*]A backup of the main GPT data structures is stored at the end of the disk, making recovery from some types of accidents easier.
Again, a non-advantage for the OP and also in practice.
> [*]Partitions have labels. These are sometimes redundant with filesystem labels, but depending on the partitioning tools you use, they can be useful in identifying the purpose of a partition.
Partitions can also have labels in MBR format. No advantage for the OP.
> [*]No linked-list data structures. MBR uses these for its logical partitions, and they can get tangled up and damaged in peculiar ways.
They get corrupted by dodgy tools, like TestDisk for example that YOU recommend to people!! Any partition table format system is vulnerable to bad tools. GPT is EVEN MORESO because it is brand new. And I have told you many times of serious problems with existing linux tools because they haven't been tested properly with GPT. And you admit yourself that the Ubuntu installer trashes other OS's boot files in the EPS 
[/list]

> This instruction only deletes the GPT's main header. The backup header remains in place, and depending on what's done with the disk, it can cause the "resurrection" of the old partition table.
<SNIP>

<snip>

---

### Post by cariboo on 2011-09-28
I would suggest both of you,  srs5694 and YesWeCan put each other on your ignore lists, as this constant bickering isn't helping anyone, and is making both of you look foolish.

It seems you have solved the op's problem, so I'm going to close this thread, if that isn't the case, please let me know, and I'll re-open it.

---

