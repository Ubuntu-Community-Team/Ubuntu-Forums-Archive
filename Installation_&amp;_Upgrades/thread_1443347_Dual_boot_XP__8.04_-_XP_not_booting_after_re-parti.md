---
title: "Dual boot XP / 8.04 - XP not booting after re-partitioning drive"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by Jacdeb6009 on 2010-03-31
Hi there,

I run XP and 8.04 on a Dell Vostro 1400.  I have been running this dual boot setup without problems now for about 18 months.

Several months ago, due to the fact that I very seldom run XP (I run a virtual machine for the two things I need to do in Windows) and the fact that I was running out of drive space (yes, you can add an external drive, but lugging these things around is a nuisance ;)) I decided to re-partition the drive.

Originally there was a Dell utility partition (sda1), Windows (sda2), and an extended partition (sda3).

The extended partition had Dell Media Player (sda4 - hidden), 8.04 root (sda5), Linux swap (sad6) and Linux home (sda7)

I got really clever and decided that since I never used the Dell utilities or the Dell Media Player, these could be deleted.  After cleaning out XP (sda2) of all unwanted software / data / rubbish, I did the following:


[LIST=1]
[*]Deleted sda1
[*]Re-sized sda2 (moved it to where sda1 started and reduced the size)
[*]Deleted sda4
[*]Moved and increased sda3 (to take up the "gap" where sda2 had previously ended and increase the size to fill up the disk)
[*]Moved sda5 to the start of the extended partition
[*]Moved sda6 to match the end of sda5
[*]Moved and increased sda7 to fill up the rest of the disk giving me more space in my /home directory
[/LIST]
All of this was done one step at a time and took a considerable amount of time.

After completing everything, I tried re-booting.  This was a disaster... :lolflag:
Grub could not find anything.  This was solved after a while and I now have a reasonable insight as to how this works.  One problem remained.  XP would not boot at all.  This was not a major problem as 8.04 was running (very well) and did everything that I needed.

I am now in a situation where I need XP running again.  I can of course use the virtual machine to do this, but the bigger problem that I have is connecting to Windows networks (never have gotten this working :confused:)

Since this is a short term assignment, I thought it may be simpler to revive XP.  I re-booted to XP again this morning to see what the error is that it spits out.

It does the following:[INDENT]Windows could not start because the following file is missing or corrupt :
<windows root>\system32\hal.dll
Please reinstall a copy of the above file.
[/INDENT]Replacing "hal.dll" of course does nothing.  Fact is that the MBR got messed up during the re-partitioning exercise and the Windows boot loader does not know where to find the things it needs to boot. (This was the same with 8.04 after the initial exercise, but this was easily fixed :p )

I have done a lot of reading in various forums about this and most seem to recommend using the Windows disk, running the repair console and then everything should be OK.

There is some advice about running ms-sys from Ubuntu, this seems to work, but needs to be done with some care as it has the possibility of hosing the windows partition if used incorrectly.

So a couple of questions.


[LIST=1]
[*]If I run the Windows repair console (assuming I can remember the admin password ](*,)) and if this actually repairs Windows, I suspect that GRUB will then be confused and will need to be re-configured again (not difficult, but need to "prepare" for this).
[*]If (1) is correct, then fixing GRUB will repair 8.04 and I will have a full working dual boot installation again.
[*]If I cannot repair this using the repair console (cannot recall admin password...) will ms-sys work and if so does this create the same problem with GRUB as running the repair console would.
[/LIST]

If you have read this far, thanks for your patience.

This is not a critical issue, since in the worst case I can install the software I need on the virtual machine running XP.  I would prefer not to do this (a) since all is installed in the XP isntallation and (b) getting this working further enhances my understanding of how these things work.  What I can not afford to do is FUBAR my 8.04 install.  This would be a catastrophe (I have backups going back to December 2009 so that a total disaster is manageable, but really should be avoided).

Any advice would be most appreciated.

Thanks!!

---

### Post by Jacdeb6009 on 2010-04-01
Hi there,

Me again.

I have now done some further work on this problem, and have drawn a blank.


[LIST=1]
[*]Downloaded Trinity Rescue Disk.
[*]Ran "winpass" to reset admin password
[*]Started up Windows using the installation disk and ran the Recovery Console
[*]Windows reports that it cannot find a valid drive and thus cannot repair anything. Do I wish to install Windows... NO!
[*]Back to Trinity ran ms-sys. No problems, but Windows still does not boot, saying that the file "hal.dll" is missing or corrupt.
[*]Tried the remaining MBR utilities on the Trinity disk. No luck.
[/LIST]


All the utilities clearly rewrite the MBR since the GRUB boot menu is gone after trying these. That is, you only get Windows trying to boot... unsuccessfully.

Fired up the 8.04 Live CD and re-installed GRUB. Machine reboots perfectly.

This is strange. Running ```
sudo fdisk -l
``` returns the following:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       19457   135315463+   f  W95 Ext'd (LBA)
/dev/sda5            2612        4570    15735604+  83  Linux
/dev/sda6            4571        4962     3148708+  82  Linux swap / Solaris
/dev/sda7            4963       19457   116431056   83  Linux

```From what I can see it appears that re-writing the MBR has resulted in the disk partitions being "re-numbered".  What was previously sda2 is now sda1 and what was sda3 is now sda2.  The partitions inside the extended partition (now sda2) have not been affected.

Changing the entry for Windows in the "menu.lst" file to now reflect hd(0,0) and then trying to boot into Windows from the GRUB menu still results in the same error as before.

I am now stumped.  Windows says that there is no "Windows" partition on the disk, various flavours of Linux say there is.  I know it's there since I can access it from Nautilus.

Clearly something is really screwed up (could be in the FAT of the NTFS partition).  Eventually I think that the simplest is to trash the Windows installation and re-install it completely from scratch.  Setting up GRUB again and all should be good.

Will do that some other time, for now the virtual Windows machine will have to do.

If any one has any ideas on this I would be happy to hear it.

Thanks!

---

### Post by Herman on 2010-04-01
If you can mount your Windows XP partition in Ubuntu or in a Ubuntu Live CD, look for the boot.ini file in the root of drive C and open it with gedit text editor.
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)[COLOR=Red]**partition(1)**[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)[COLOR=Red]**partition(1)**[/COLOR]WINDOWS="Microsoft Windows Xp Home Edition" /fastdetect
```Check to see if the partition number shown in boot.ini matches the number of the Windows partition according the a partition editor such as GParted, or fdisk.

You may use gedit text editor to edit the partition number, but avoid making any new lines, (don't use your return key), because the invisible carriage return signal is different in Windows and putting a Linux newline in will 'corrupt' the file as far as Windows is concerned).
I'm not sure how Windows numbers its partitions but I do remember there is something different about that, so you might need to guess, but I think yours probably says 2 or another number and you should probably edit it to say 1. I'm only guessing.

Alternatively, if you have a Windows XP installation CD, you can boot into a Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and run [COLOR=Black][FONT=Bitstream Vera Sans Mono][FONT=monospace]bootcfg /rebuild
That command will automatically generate you a new boot.ini file.
[/FONT][/FONT][/COLOR]

---

### Post by Jacdeb6009 on 2010-04-01
Hi there Herman,

Thanks for your response!!

I will definitely take a look at what the "boot.ini" file has in it.

That's the weird thing.  I can mount the drive in Linux, read, write, do whatever I like, but Windows will not boot it.

The recovery console does not help me, since I cannot get it to run.  Windows runs through the whole setup process up to the point where you select to install, recover or quit.  When you select "Recovery Console" it returns an error message basically saying that there is no valid Windows drive on the machine.

Strange since the non-Windows utilities I have used so far, all see this as Windows...

(Maybe Microsoft just don't want me to have "their" Windows cohabiting with "our" Linux :p)

Anyway, will try this out and let you know my progress a bit later today.

BTW, you various GRUB and other bootloader sites are GREAT!  This is what has saved my hide a couple of times in the past!!

Best regards,

---

### Post by Jacdeb6009 on 2010-04-01
Hi there Herman,

I checked the Windows boot.ini file and indeed it was pointing at the wrong partition (this of course as a result of the renumbering.  Still don't understand why it wouldn't boot before the numbers all changed, anyway that's how it is.

I changed the boot.ini file as you indicated and lo and behold Windows booted; or, tried to.  It hangs.  Tried booting in safe mode, safe mode command prompt, previous known good configuration, all without success.

On each occasion the boot process hangs.  Worse, of course the only way to restart the machine was to "pull the plug"... result is that now the disc cannot be mounted by Linux as it sees the NTFS "in use" flag as set.

Anyway, I will still "play" with it for a while, but I suspect that ultimately I will reformat and re-install (probably a good idea since Windows was getting really slow and unstable at the point I installed 8.04).

Still, thanks for you help.  It certainly solved the problem of not being able to get Windows booting.  In the process, I have again learnt a whole lot more about computers and OS's in general (including the fact that Linux rocks, but then we knew that :) )

Best regards,

Jac.

---

### Post by Herman on 2010-04-01
You probably need to run CHKDSK on it, (a file system check). That will probably fit it. 

You'll need a Windows XP 'Installation' CD for that.

If you have a Windows XP Installation CD, you can boot it into a [Windows Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), choose 1. (if that's your XP partition), type your admin password and  issue the command: CHKDSK /R

If you don't have one of your own Windows XP 'Installation Disk' you'll need to go asking around, looking in second hand shops and markets until you find one.
It's ridiculous that owners of computers that come with Windows installed in them don't always come with a Windows 'Installation' CD, because there are times when you *need* that CD to fix Windows with. Unless you pay money and like sharing it to get somebody else who does have a Windows XP CD to fix it for you. 

The wise and kind people at [ntfsprogs]("http://www.linux-ntfs.org/doku.php?id=ntfsprogs") are working on an open source version of CHKDSK, *[ntfsck]("http://www.linux-ntfs.org/doku.php?id=ntfsck"),* but I'm not sure how long before it will be ready, their website just says it's not available yet.

---

### Post by justanothergreysky on 2010-04-01
I would suspect that now the boot.ini is fixed, that the "Windows Repair" procedure will work properly when booting from the Windows XP CD, and you may be able to repair it with that.

---

### Post by Jacdeb6009 on 2010-04-02
Hi Herman,

The issue about not having a Windows install disk and various other licensing issues that I strongly disagree with was one of the main reasons for switching to Linux, and a happy day that was.

Fact is that whether we like it or not, we live in a "Windows world" and sometimes it is a necessary evil to be able to run Windows.

I have a disk, but previously it would not even read the hard drive at all.

I will try this again over the weekend (when I have some more time) and see if Windows can be revived.

I tend to share your and justanothergreysky's opinion that this should sort the problem.  It has gotten to the point where this is now more or less "academic".  It has become a matter of "pride" to get it working, not so much necessity anymore.  As I said previously, in the worst case I can always re-format and re-install.  But damn it, that way I don't learn anything :D

Thanks and best regards,

---

