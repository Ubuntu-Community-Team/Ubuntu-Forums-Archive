---
title: "Multiple boot XP/Ubuntu + other linux"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by alainhenry on 2005-06-08
I have a working system with WinXP and Ubuntu Hoary, using GRUB for dual boot. 

I recently tried to install other linux distros on the same machine (Mandriva LE 2005, KUbuntu, Fedora Core 3).  The install always goes fine, but a problem always appear when I try to reboot the system in the new distro.  For example, installing Fedora C3, which uses GRUB too.  The system stops immediately after reboot, at GRUB startup, and shows a black screen with "GRUB" on the screen, and then freezes. I tried booting from a grub boot floppy, and it did not recognise the partition hda10 I used to install FC3 (the command root (hd0,9) froze the machine).  Fortunately, I can use the GRUB floppy to reset  the system to XP/Hoary, which keeps working fine.  
I had the same problem when trying to install Mandriva LE2005 and KUbuntu.

Any idea ? Any information useful to help solve this ?

Thanks

Alain

---

### Post by mingus on 2005-06-08
There are a number of forum threads on this.  I recall seeing one with a similar problem to yours involving Fedora, in just the last few days.  First good step is to search.

If you don't find your answer, post back your /boot/grub/menu.lst file.  If you are trying diff distros, you will need to choose just one to manage grub for everything because the distros use grub differently from one another.  Debian, like Fedora and SuSE, use auto-generators and sometimes miss seeing other distros.  For what you are doing, you may need to manually manage the menu.lst file.

---

### Post by alainhenry on 2005-06-11
Thanks for your answer.  I did not find anything to solve my problem, so I post here the relevant parts of menu.lst, as well as fstab and the result of fdisk -l.  Ubuntu root is on hda5, winXP on hda1, FC3 on hdb5.  

Thanks for any help you could provide, and have a good week-end

Alain


1) Additional info: 

At boot, I have an error message for hdb5, telling me this: 

fsck-ext3: filesytem has unsupported feature(s) (/12)
e2fsck: get a newer version of e2fsck!
 

2) 
# excerpts from menu.lst
## ## End Default Options ##
# AH: This is the Debian installer Ubuntu entry, which works

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

[snip] 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
# AH: This is the Debian installer WinXP entry, which works

title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# AH: These are the entries I tried for Fedora Core 3 and do not work.  
# AH: The system freezes after displaying the "kernel" line

title		Fedora Core 3 on hdb5 
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.9-1.667 ro root=/dev/hdb5 rhgb quiet
initrd		/boot/initrd-2.6.9-1.667.img
savedefault
boot

title		Fedora Core 3 on hdb5(LABEL)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.9-1.667 ro root=LABEL=/12 rhgb quiet
initrd		/boot/initrd-2.6.9-1.667.img
savedefault
boot


3) fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    umask=0222      0       0
/dev/hda8       /media/echange  vfat    codepage=850,iocharset=iso8859-15,umask=0   0   0
/dev/hdb5       /media/hdb5     ext3    defaults        0       2
/dev/hdb6       /media/hdb6     ext3    defaults        0       2


4) Result of fdisk -l command

Disk /dev/hda: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       40635    20480008+   7  HPFS/NTFS
/dev/hda2           40641      238202    99570870    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/hda5           40641       60005     9759456   83  Linux
/dev/hda6           60005      137509    39062016   83  Linux
/dev/hda7          137509      141382     1951866   82  Linux swap / Solaris
/dev/hda8          141383      161861    10321384+   b  W95 FAT32
/dev/hda9          161862      196398    17406616+  83  Linux

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       61454    30972784+  83  Linux
/dev/hdb2           61455      238215    89087544    f  W95 Ext'd (LBA)
/dev/hdb5   *       61455       81771    10239736+  83  Linux
/dev/hdb6           81776      102096    10241406   83  Linux

---

### Post by stoneguy on 2005-06-11
> root=LABEL=/12Huh?

Entry looks like pretty much a dupe of the one just above. Try commenting the lower one out.

---

### Post by mingus on 2005-06-12
I didn't catch anything other than what stoneguy pointed out; what is "root=LABEL=/12"?

In Debian's use of grub, other distros are explicity pointed at their init and kernel, like the default.  However, in some distros (like SuSE) all other distros are chain loaded, like Windows is.  This does require that grub be installed onto the /boot partition of the other distro, so what is happening is one boot loader is handing off to another, in this case, one grub installation to another distro's grub installation.  I have found this method to work just fine, so if the change above doesn't work, you might try this.

---

### Post by vince-ubuntu on 2005-06-12
for you problem with e2fsck, you might want to check this:

[http://www.mail-archive.com/trilug@trilug.org/msg26479.html](http://www.mail-archive.com/trilug@trilug.org/msg26479.html)

Vince

---

### Post by alainhenry on 2005-06-13
[QUOTE=stoneguy]Huh?

Entry looks like pretty much a dupe of the one just above. Try commenting the lower one out.[/QUOTE]

Yeah, that seemed strange.  So i copied the entry I got from the menu.lst from fedora, and I copied it again but replaced that strange entry by /dev/hdb5, where root is located.  

Anyway, both these menu choices give the same result.  

Alain

---

### Post by mingus on 2005-06-13
Again, the only suggestion I have is to try chain-loading Fedora.  Install the grub boot loader on the Fedora /boot partition, and then call it from Ubuntu grub.

---

### Post by alainhenry on 2005-06-14
Like this ?

title		Fedora Core 3 on hdb5
root		(hd1,4)
savedefault
makeactive
chainloader	+1

I got an error 12 : invalid device requested

Alain

---

### Post by fmcdee on 2005-06-14
I've been following your discussion and WAS about to load Ubuntu, Kubuntu, and Linspires after XPro, but I wouldn't know what to do if I had a boot problem because of distro conflicts.  I was told that loading Linspire last would allow it to give choice for distro during bootup.  Any thoughts you'd like to share will be appreciated.  I can't reach the Newbie Level yet but do hope to improve. Tks

---

### Post by mingus on 2005-06-14
Alain,

Take a look at the following, which seems exactly like what you want to do:

[http://enterprise.linux.com/enterprise/04/12/23/2033238.shtml?tid=129&tid=47](http://enterprise.linux.com/enterprise/04/12/23/2033238.shtml?tid=129&tid=47)

I notice the "label" command here which I am unfamiliar with, but this supposedly works.

I am continuing to look into this.  I have grub multi-booting on 2 machines, but it still occasionally does something unexpected.

---

### Post by mingus on 2005-06-14
[QUOTE=fmcdee]I've been following your discussion and WAS about to load Ubuntu, Kubuntu, and Linspires after XPro, but I wouldn't know what to do if I had a boot problem because of distro conflicts.  I was told that loading Linspire last would allow it to give choice for distro during bootup.  Any thoughts you'd like to share will be appreciated.  I can't reach the Newbie Level yet but do hope to improve. Tks[/QUOTE]

All three use the Debian method of installing the boot loader.  Theoretically, each installation should see what already exists and put that into the control file.  But of course, only the last distro would have all 4.

XP must be installed first, and must be on the first partition of the first disk.  It is critical that you have boot recovery media, such as the XP CD or a boot floppy.  This is true whether you add the distros or not.

There are different techniques that can be used for dual or multi booting.  One uses the Windows loader.  On the Linux side, you can use grub or lilo.  And there are several methods with each.  Just as would be true if you were adding more Windows installations (like a second XP, or W98 with XP, for example), it is important to investigate how this is done and plan it carefully.  The wiki, forums, and google are your guides.

---

### Post by fmcdee on 2005-06-15
O:) Tks for the info.  What is Wiki? Tks.

---

### Post by alainhenry on 2005-06-15
Wiki is located at [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

Wikiwiki means quick in the language of Hawaii.  A wiki is a set of web pages that each can be edited by each visitor (see [http://en.wikipedia.org/wiki/Wiki)](http://en.wikipedia.org/wiki/Wiki)).  ideal for cooperative work.  

Alain

---

### Post by alainhenry on 2005-06-15
[QUOTE=mingus]Alain,

Take a look at the following, which seems exactly like what you want to do:

[http://enterprise.linux.com/enterprise/04/12/23/2033238.shtml?tid=129&tid=47](http://enterprise.linux.com/enterprise/04/12/23/2033238.shtml?tid=129&tid=47)

I notice the "label" command here which I am unfamiliar with, but this supposedly works.

I am continuing to look into this.  I have grub multi-booting on 2 machines, but it still occasionally does something unexpected.[/QUOTE]

I followed the advice from this link, but still got a freeze at the kernel stage.  
I also tried to install MEPIS, with GRUB on the MBR.  MEPIS-installed GRUB freezes at boot time.  I recovererd the machine for the xth time with a grub floppy.

Despair hits me

Alain

---

### Post by mingus on 2005-06-15
Have you tried to execute the commands interactively from the grub menu, by getting into the grub shell?

---

### Post by mingus on 2005-06-15
[QUOTE=alainhenry]Like this ?

title		Fedora Core 3 on hdb5
root		(hd1,4)
savedefault
makeactive
chainloader	+1

I got an error 12 : invalid device requested

Alain[/QUOTE]

I just shooting in the dark here . . . however, I don't think you want "makeactive"; this is only for Windows because it requires its boot partition to be active.  And I don't use "savedefault" on my chainloader stanzas.

Grub's explanation for error 12 is "This error is returned if a device string is recognizable but does not fall under other device errors."

I noticed that the info command for grub is not in Ubuntu by default; you have to install it (grub-doc).  The man pages are very limited.  But the info has a lot more detail, including the error messages.

---

### Post by alainhenry on 2005-06-16
I keep struggling, thanks for the help.  I will try your suggestions

Alain

---

### Post by mingus on 2005-06-17
One other thought . . . 

Make sure the order of hard drives in device.map is the same as the boot sequence in the BIOS setup.  The purpose of the device.map is to (a) provide the optional cross-referencing between linux to grub naming and (b) to tell grub the boot sequence because grub cannot read the BIOS.

---

### Post by alainhenry on 2005-06-22
Just tried it with new fedora core 4.  Installed the bootloaderon the root of FC4 (/dev/hdb5), made sure device.map pointed to the 2 drives, and had the following item in menu.lst 

title Fedora Core 4 on hdb5
root (hd1,4)
savedefault
#makeactive
chainloader +1

I still get error 12.  I tried adding the makeactive.  Then GRUB recognises hdb5 but  freezes after displaying GRUB on the screen.  

I get similar results when trying grom the grub prompt.

I also tried with "Force LBA32" as FC4 grub boot option, but with the same results. 

I'm lost again

Alain

---

### Post by alainhenry on 2005-06-22
[QUOTE=vince-ubuntu]for you problem with e2fsck, you might want to check this:

[http://www.mail-archive.com/trilug@trilug.org/msg26479.html](http://www.mail-archive.com/trilug@trilug.org/msg26479.html)

Vince[/QUOTE]

Works fine indeed, using the command debugfs -w /dev/hdb5 instead of the one mentioned in the link

Thanks

Alain

---

### Post by mingus on 2005-06-22
[QUOTE=alainhenry]Just tried it with new fedora core 4.  Installed the bootloaderon the root of FC4 (/dev/hdb5), made sure device.map pointed to the 2 drives, and had the following item in menu.lst 

title Fedora Core 4 on hdb5
root (hd1,4)
savedefault
#makeactive
chainloader +1

I still get error 12.  I tried adding the makeactive.  Then GRUB recognises hdb5 but  freezes after displaying GRUB on the screen.  

I get similar results when trying grom the grub prompt.

I also tried with "Force LBA32" as FC4 grub boot option, but with the same results. 

I'm lost again

Alain[/QUOTE]

bummer! . . . time to re-group . . . sorry if any of this is repetition . . .

The errors seem to indicate that the boot partition, or stage2 on the boot partition, is not being found.  Usually this is due to a wrong path or an inconsistency between how boot and the BIOS see the drives.

When you boot Ubuntu, have you tried doing 'c' to go to the grub the shell and entering the FC4 boot commands directly (root, kernel, initrd, boot)?

Have you tried removing the rhgb from kernel line?

Have you tried to install grub from a terminal using explicit paths?  Do $sudo grub and then:
>install (hd1,4)/boot/grub/stage1 d (hd0)  (hd1,4)/boot/grub/stage2 p (hd1,4)/boot/grub/menu.lst

Do you have LBA set for the drives in the BIOS?

Does your BIOS recognize the full capacity of the drives?

Is your boot sequence the same as your BIOS drive sequence?

Are you using a drive overlay or anything else special/unusual with the drives?

Have you tried using LILO instead?

I have seen multi-boot linux articles, I would google that . . .

All I can think of right now.

---

### Post by alainhenry on 2005-06-23
Thanks, I'll try again on a systematic basis... though I'm not optimistic.  
I don't know when yet.  Don't expect news before a few days

Have a nice day

Alain

---

### Post by alainhenry on 2005-08-06
Hello, sorry to have taken so long to get back to this thread.  I had few time to continue the struggle.  I tried again a few tricks, to no avail.  

Then I decided to reformat hdb with the Win XP install Disk.  Once done, I installed Mandriva LE2005, set up the bootloader (lilo) on the root of Mandriva (hdb5) and added the lines

title Mandriva on hdb5
root (hd1,4)
savedefault
chainloader +1

And bingo, I could boot Ubuntu and Mandriva.  

This does not explain a lot, but at least it works.  I hadaa asimilar problem when I bought the PC.  I installed Ubuntu and then it would boot on any Microsoft cdrom (at least a dos floppy and the winXP cdrom).  My PC vendor told me that the formatting of the HD by a non-microsoft system was slightly different than what microsoft expected, and that this caused the trouble.  Don't know if it makes sense, but I reformatted the hard disk with the Win XP cdrom on anoher PC, and that solved my problem.  

Could this be the sign that Ubuntu formatting has a difference ?

Thanks to all and to Mingus in particular for taking the time to investigate this anyway.

Alain

---

### Post by mingus on 2005-08-08
[I]This does not explain a lot, but at least it works.  I hadaa asimilar problem when I bought the PC.  I installed Ubuntu and then it would boot on any Microsoft cdrom (at least a dos floppy and the winXP cdrom).  My PC vendor told me that the formatting of the HD by a non-microsoft system was slightly different than what microsoft expected, and that this caused the trouble.  Don't know if it makes sense, but I reformatted the hard disk with the Win XP cdrom on anoher PC, and that solved my problem.  

Could this be the sign that Ubuntu formatting has a difference ?[/I]

Yes, there is a difference.  This problem is very complex technically, and usually does not happen.  But when it does, the only solution is to directly edit the partition table or to rebuild the partitions.  There was probably a boundary overlap that prevented grub from finding the boot sector.  Users also get confused between partitioning and formatting.  Actually, the problem is not Ubuntu or Linux, but W$ - it does strange, proprietary things with the table, and marks partition boundaries differently than other OS's.  W$ is very hostile to anything else on the disk.

*Thanks to all and to Mingus in particular for taking the time to investiagte this anyway.*

You're welcome.  Sorry I wasn't more help.

---

### Post by buster on 2005-08-08
Something that doesn't seem to have come up in the discussions. Here's how I did my first multidistro computer many years ago.

1. Install Windows.
2. Install Distro A and write grub to the mbr.
3. Check that these both work.
4. Install Distro B and write grub to a FLOPPY. Test booting with the floppy. Make a backup copy of the floppy.
5. Install Distro C and write grub to a floppy etc, etc etc.
6.Repeat steps 4 and 5.
7. AT YOUR LEISURE play with the grub menu list in Distro A.

You can boot everything. And you are safe. 

(I actually have a simplified slide presentation for our group of doing this but I used  lilo back then.)

---

### Post by mingus on 2005-08-08
[QUOTE=buster]Something that doesn't seem to have come up in the discussions. Here's how I did my first multidistro computer many years ago.

1. Install Windows.
2. Install Distro A and write grub to the mbr.
3. Check that these both work.
4. Install Distro B and write grub to a FLOPPY. Test booting with the floppy. Make a backup copy of the floppy.
5. Install Distro C and write grub to a floppy etc, etc etc.
6.Repeat steps 4 and 5.
7. AT YOUR LEISURE play with the grub menu list in Distro A.

You can boot everything. And you are safe. 

(I actually have a simplified slide presentation for our group of doing this but I used  lilo back then.)[/QUOTE]

I also recommend this conservative approach.  All I would add is that, once one is sure the installation is stabilized, to install grub into the boot sector of distro B & C, and then chain-load from A rather than using explicit kernel stanzas.  IMHO that's cleaner.  Only problem is, lotta systems now don't come with a floppy, and users don't receive W$ install media either any more . . . if for whatever reason the multi-boot setup gets borked, most don't know how to work their way out of it.

---

### Post by blastus on 2005-08-09
Man you guys have complicated setups!  :-?  Can you make boot CDs instead of floppies to boot to the other OSs? 

What I do know is that you can only have 4 primary partitions on an EIDE drive. If you create more than 4 partitions, the first 3 will be primary and 4th will be a special extended partition that contains logical partitions. I think having an extended partition makes things more ?complicated? because the MBR doesn't contain the table for the extended partition. I believe the table for the extended partition is stored in the boot sector of the first logical partition which is pointed to by the entry for the extended partition in the partition table in the MBR. This means that if you have an extended partition the partitions aren't totally independent of each other. CORRECTION: the MBR contains a link to the first logical partition, then the 1st logical partition contains a link to the 2nd logical partition and so forth...everything is chained.

Having an extended partition may be causing your boot loader problems, I don't know. If Windows is on the first partition of the first drive I don't see how it can mess up the partition table in the MBR or the extended partition table once Windows has been installed. Of course if you reinstall Windows then it will whack the boot strap code in the MBR but it will leave the partition table in the MBR intact. I believe there's only a couple of bytes in the MBR that Linux can't use because Windows uses them exclusively. This I believe is the volume serial number for the drive and something else, I don't remember. To keep things simple I never have more than 4 partitions on a drive. This way I know for sure that I can nuke one partition without it somehow or mysteriously affecting the others if that's possible. :-?

---

### Post by mingus on 2005-08-09
You are right . . . sort of.  There are really two different, although related, issues above.  The first is the difference in how W$ uses the MBR, the boot sector, and its "system partition".  Multi-booting problems usually arise from doing the setup in the wrong sequence or not installing grub correctly.  But sometimes even a normal activity like changing the drive letter will corrupt the table.  Re primary vs extended, W2K/XP's system partition must be a primary but the OS can reside on any other partition, although usually the same partition is used and therefore it must be a primary.  With grub or lilo, this is *not* required because both grub and lilo do the MBR-to-boot sector hand-off differently.

The problem Alain discovered was a conflict between partition table entries due to be written to by both DiskManager and the Linux partitioner.  DM calculates geometries differently and writes partition start/end addresses to the table, this goes back to DOS which was long recognized as being faulty.  Usually doesn't matter because nothing else is using the table (but you do get anomalies like DM reporting one drive capacity while msinfo reports another).  Linux only writes a starting address, and also uses a different (correct) geometry algorithm.  Actually, Linux doesn't care that much (this is all virtual anyway) except for the partition start sector.  If DM writes to the table after Linux has been installed (W$ sometimes re-writes the *whole* table not just the entry being changed), the location of sector 1 (the boot sector) may change and cause grub to fail.

Using a boot floppy gets around some of this because the boot loader and boot sector are all on the diskette.  There is no MBR code handing off to bootstrap bridge (ntdetect.com or grub stage1.5) to boot loader (ntldr or grub stage2).  As far as creating a bootable CD, yes that can be done using the El Torito standard or by writing the MBR code to sector 1 of the CD, both techniques requiring you have the code segment in a file and know how to do this.  The CD replaces the MBR, but the rest of bootstrap happens the same from the hdd.  But the floppy is different; it is self-contained.  So bottom line, the boot floppy is much easier to create *and* is more reliable to boot from.

---

