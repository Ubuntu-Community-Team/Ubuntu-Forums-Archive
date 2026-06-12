---
title: "The Bootloader Experiment Thread"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by Herman on 2010-12-18
The aim of this thread will be to learn more about boot loaders so we can improve our help to people with boot loader problems.
I'm hoping we can get a good collection of boot loader related experiments all in one thread so we can refer to them later whenever we need to.
 
Is there something you've always been curious about? Do you know of a myth about boot loaders you want to bust? 
Have you a spare ***puter you don't mind risking making temporarily unbootable or even risking the possibility of hosing an operating system and having to re-install to prove something you wanted to know about boot loaders?

It would be nice if we can keep the format of these experiments reasonably structured, for example, state the aim of the experiment, what you did, what the results were and conclusions.
If you don't feel like doing it that way just add your experiment anyway, all reasonably sensible contributions are wel***e.

**INDEX:**

[Post #2 Installing GRUB in a Windows 7 /boot Partition]("http://ubuntuforums.org/showpost.php?p=10252336&postcount=2") - (just the grub files, not the boot.img) - by Herman

[Post #3 Windows7 Installed last on sda9]("http://ubuntuforums.org/showpost.php?p=10252455&postcount=3")   - by owiknowi

[Post #5 Windows XP Boots In Any Physical Location On A Hard Disk]("http://ubuntuforums.org/showpost.php?p=10253949&postcount=5") - by Herman 

[Post #10 GRUB2 Can Boot Windows Recovery Partition in USB and Make Cool Linux Utility Disk By Adding Linux ISOs]("http://ubuntuforums.org/showpost.php?p=10254553&postcount=10") - by oldfred

[Post #13 Windows7 Boot Sector Trashed by Installing GRUB's boot.img to it, Then Recovered with 'bootrec /fixboot']("http://ubuntuforums.org/showpost.php?p=10255062&postcount=13") - by Herman

[Post #19 Booting Windows XP in a Non-first Partition Number in the Middle of the Hard Disk]("http://ubuntuforums.org/showpost.php?p=10255411&postcount=19") - by Herman 

[Post #20 Windows XP Booting in a Logical Partition by GRUB Boot Loader near the end of the Hard Disk]("http://ubuntuforums.org/showpost.php?p=10255691&postcount=22") - by Herman

[Post #23 Links to Some Important Information in Old Threads]("http://ubuntuforums.org/showpost.php?p=10256375&postcount=23") - by oldfred

[Post #25 How The Mere Act of Adding A New Partition Can Cause Windows XP Boot Failure]("http://ubuntuforums.org/showpost.php?p=10258012&postcount=25") - by Herman

---

### Post by Herman on 2010-12-18
**Installing GRUB in a Windows /boot Partition**

**Aim: **
To see if GRUB can be installed in a Windows 7 /boot partition (ntfs) without any harmful effects on the Windows system.

**Method: **
The Windows /boot partition was mounted when I clicked on it in 'Places', 'Removable Media', 'System Reserved'.
It was mounted as /media/System\ Reserved/ because 'System Reserved' is the file system label it was given at installation time.

The Windows /boot partition already has a folder in it named  'Boot', with an upper case 'B', and the grub-install command should create a new folder and call it 'boot', (with a lower case 'b', and it should make a directory named 'grub' inside that and fill it with GRUB files.
GRUB's boot.img and core.img will also be installed somewhere.
It would render Windows unbootable of course if I installed it to a Windows boot sector, but it's a great idea to install GRUB to MBR in the first hard drive, so that's what I decided to do.

A possible hazard another Ubuntu Web Forums member, , pointed out was that since Windows is not case sensitive like Linus is, it would not be able to tell the difference between a directory named 'Boot' and one called 'boot', and that might confuse the Windows boot loader.
To avoid that problem, I renamed the Windows /Boot directory to /boot, (I just changed the B to a b).

I tried to use the grub-install command to install GRUB but the grub-install command kept producing an error message about /media/System\ Reserved/ not being a directory.
Thinking that might have something to do with the white space in the file system label I opened GParted and replaced the white space in the file system label with an underscore instead.
That worked and I was able to run grub-install, 
```
sudo grub-install --root-directory=/media/System_Reserved /dev/sda
```

That worked and I opened the newly created /media/system_reserved/boot/grub to see that it was full of GRUB files as expected.

I rebooted, and as expected I was able to boot both Windows and Ubuntu perfectly normally.

**Conclulsions:**
This experiment shows that as GRUB doesn't necessarily hurt Windows as long as the Windows boot sector is not  damaged. If GRUB was installed to the Windows boot sector, then it would case Windows to be unbootable until repairs could be made.
I would not recommend any one go out of their way to try this experiment in a Windows system they care about. This may be useful to know because it has happened once that a user accidentally install GRUB to their Windows 7 /boot partition in this way, (I don't know how they could have managed to do that by accident, but anyway), and did not need to re-install  Windows because of it, which surprised some people. This might also be useful for someone with a  maximum number of partitions problem and wants to add a 'Dedicated GRUB Partition but can't have any more partitions. GRUB installed in the Windows 7 /boot partition this way could be used as a 'Dedicated GRUB Partition'.

**Further work:**
I wouldn't want anyone else to repeat this experiment in a Windows system they care about, but I wonder if I was I just lucky or will this work with most Windows operating systems?

---

### Post by owiknowi on 2010-12-18
nice idea herman!

till now i always used grub <2 because i could always manually edit menu.list.
have to dive into grub 2 someday so maybe this is the right moment?

first i used to know a trick to restore the mbr when only windos should be able to boot: fdisk /mbr
this erased the mbr and only windos was able to boot, again.

setting a new disklabel erases the whole existing partitioning.

also the partitioning was of some importance till windos7: it had to be installed first on a primary partition at the beginning of the hdd.
now i have one installed at the end of the hdd and after installing several linuxes.

partition table looks like this:
sda1: ext4 (primary), sda2: swap, sda3: (extended) with 8 logical volumes sda4-sda8.
last and least an other primary partition sda9: ntfs with boot flag.

i've installed windos7 last on sda9 (set flag as boot) and there it went: of course the mbr was taken over by windos7 and it even changed the partition table.

all partition numbers in the extended partition have moved up one place!
so sda8 became sda9.

the bootloaders of all linuxes i've installed in their root partition and i use easybcd for windos as bootloader.
that's wroooong to speak with mr. e. cartman.

what i want is that ubuntu on sda1 - my default os - should take over the bootloader.
the new bootloader should be configured from here (i install more or less one or two os a week for test purposes).

the gui from easybcd is nice but not required, gedit is fine too. but i don't know grub2 yet.

so how do i go about from here, herman? is this something we can work/test with? if not just let me know.

btw. i only use windos7 to be able to take a quick look at it when a windos question comes up.
i've chosen to install it on a primary partition after the extended and at the end of the hdd to be able to erase it when i want, without messing up the rest.

---

### Post by Rubi1200 on 2010-12-18
I'd also like to add that I think this is an excellent idea.

Thanks Herman for all the hard work, guides, and other great things you do for the Ubuntu community and Linux in general.

---

### Post by Herman on 2010-12-18
> also the partitioning was of some importance till windos7: it had to be  installed first on a primary partition at the beginning of the hdd.:D Thanks owiknowi,

Windows XP Boots In Any Physical Location On A Hard Disk

**Myth: **
Windows XP needs to be installed at the start of a hard disk or it won't boot.

**Aim:**
This experiment should show that (at least in one of my computers), it's relatively trivial to move Windows XP to any physical location on the hard disk and it will still boot right up without any problems.

**Method:**
I used the most up to date version of GParted I can get my hands on, GParted 0.7.0, in Parted Magic Live CD version 5.7.
I have already done this same experiment years ago with an older version of GParted and it worked fine back then, so it should still work now.

So I booted up my Acer T310 with Windows XP Home Edition in the first hard disk with Parted Magic 5.7 and opened GParted.

NOTE: One thing unusual about this Windows XP install is it begins at sector 2048 instead of sector 63, which is a result of an earlier experiment to see I could achieve the new partition alignment for Windows XP with GParted.
That kind of means Windows XP had already been moved, so I expect moving it further isn't going to make any difference, but we'll see.

NOTE1: My old Windows XP installation still uses the old FAT32 file system. It shouldn't make any difference for the purposes of this experiment, but you never know. Some day I (or someone) should try the same experiment with it formatted to NTFS just to make sure.

NOTE2: I have already done this same experiment already a long time ago and it worked the last time I did this, so I expect this will tend to confirm my earlier findings.

1. I resized my Windows XP from 74.53 GiB, occupying just about the entire 80GB Hard disk, to as small as I can shrink it, at the moment 20000 GB will have to do, it must have some files in it.
NOTE: It took a lot longer time to move Windows while it contains files, I would have been better off copying all the files out some other drive first. There's nothing on there I don't have a back up of though. (Of course).

2. I moved the 20GB Windows XP all the way to the other end of the hard disk. GParted flashed up a warning that moving an operating system might cause it to fail to boot properly. I ignored the warning because I think it applies mainly to Windows7 and Vista, and anyway I'm confident I can fix it almost no matter what. Besides, I don't care about Windows much anyway. (LOL).
(I know some people do though, new users, who we're conducting these experiments for to try to help them better).

3. I went outside and mowed my back yard while the operation was under way and when I came back in for breakfast the operation had successfully completed. I rebooted Windows XP via my GNU/GRUB installed in my Ubuntu hard disk.
The result was Windows XP booted up just fine on the very first attempt and no boot loader repairs were needed.

4. I moved the entire Windows partition again with GParted to an area around the middle of the hard disk and again it booted up via GRUB from my Ubuntu installation in the other hard disk without any problems at all.

5. I re-installed the Windows boot loader to MBR before moving Windows XP back to the start of the disk to see if the Windows boot loader will be able to boot Windows when the partition is moved without requiring repairs first.

6. I rebooted Windows in the middle of the first hard disk by its own boot loader, (not using GRUB at all). I did that by booting a Windows XP Installation CD to a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and applying the command 'fixmbr'.

7.   Once again, after GParted moved the Windows XP partition, this time back to where it was when I started, (back to sector number 2048), Windows XP booted as per normal.

**Conclusions: **
It doesn't seem to matter if my Windows XP partition starts close to the start of the hard disk or in the middle somewhere or near the end of the hard disk it seems to be bootable.
I'm not sure about other people's computers, maybe some people have a slightly different Windows XP than I do. 

**To Do:** 
> it had to be  installed first on a primary partitionThis is another myth. Windows XP does not need to be in a primary partition, or at least mine doesn't, but that's a subject for another experiment I'll try later on, and it also doesn't seem to matter what partition number it has either, providing we fix boot.ini. I'll demonstrate that in a future experiment too. :)

---

### Post by kansasnoob on 2010-12-18
> **Herman said:**
> **Installing GRUB in a Windows /boot Partition**

**Aim: **
To see if GRUB can be installed in a Windows 7 /boot partition (ntfs) without any harmful effects on the Windows system.

**Method: **
The Windows /boot partition was mounted when I clicked on it in 'Places', 'Removable Media', 'System Reserved'.
It was mounted as /media/System\ Reserved/ because 'System Reserved' is the file system label it was given at installation time.

The Windows /boot partition already has a folder in it named  'Boot', with an upper case 'B', and the grub-install command should create a new folder and call it 'boot', (with a lower case 'b', and it should make a directory named 'grub' inside that and fill it with GRUB files.
GRUB's boot.img and core.img will also be installed somewhere.
It would render Windows unbootable of course if I installed it to a Windows boot sector, but it's a great idea to install GRUB to MBR in the first hard drive, so that's what I decided to do.

A possible hazard another Ubuntu Web Forums member, , pointed out was that since Windows is not case sensitive like Linus is, it would not be able to tell the difference between a directory named 'Boot' and one called 'boot', and that might confuse the Windows boot loader.
To avoid that problem, I renamed the Windows /Boot directory to /boot, (I just changed the B to a b).

I tried to use the grub-install command to install GRUB but the grub-install command kept producing an error message about /media/System\ Reserved/ not being a directory.
Thinking that might have something to do with the white space in the file system label I opened GParted and replaced the white space in the file system label with an underscore instead.
That worked and I was able to run grub-install, 
```
sudo grub-install --root-directory=/media/System_Reserved /dev/sda
```

That worked and I opened the newly created /media/system_reserved/boot/grub to see that it was full of GRUB files as expected.

I rebooted, and as expected I was able to boot both Windows and Ubuntu perfectly normally.

**Conclulsions:**
This experiment shows that as GRUB doesn't necessarily hurt Windows as long as the Windows boot sector is not  damaged. If GRUB was installed to the Windows boot sector, then it would case Windows to be unbootable until repairs could be made.
I would not recommend any one go out of their way to try this experiment in a Windows system they care about. This may be useful to know because it has happened once that a user accidentally install GRUB to their Windows 7 /boot partition in this way, (**[COLOR="Red"]I don't know how they could have managed to do that by accident[/COLOR]**, but anyway), and did not need to re-install  Windows because of it, which surprised some people. This might also be useful for someone with a  maximum number of partitions problem and wants to add a 'Dedicated GRUB Partition but can't have any more partitions. GRUB installed in the Windows 7 /boot partition this way could be used as a 'Dedicated GRUB Partition'.

**Further work:**
I wouldn't want anyone else to repeat this experiment in a Windows system they care about, but I wonder if I was I just lucky or will this work with most Windows operating systems?

It used to happen a lot before I filed this bug report (and followed up by screaming and crying):

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

Since the situation has since been resolved I trashed my old screenshots but basically anytime a package update would trigger 'update-grub' it would present a shot like this:

[http://ubuntuforums.org/attachment.php?attachmentid=155778&d=1273197137](http://ubuntuforums.org/attachment.php?attachmentid=155778&d=1273197137)

Where all devices would be displayed, and the text would say, "if in doubt select all". It's actually displayed in the screenshot but that's the general gist of it :)

For a very long time this was the preferred method of fixing it:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But now you make me wonder how related this may be:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by Herman on 2010-12-18
:D @ kansasnoob, thanks for your input. 

Maybe you missed something there, that experiment is about what happens when we install *all except the boot.img* of GRUB to the Windows partition.
It's not about what happens if we accidentally install the boot sector, which is what you seem to be on about, and that's a different subject for another experiment later on maybe.

Unless you'd like to help by contributing an experiment of your own to prove what happens when GRUB is installed to the Windows boot sector if that's what you want to talk about. 
You might describe what error messages you see if any or what behavior you observed, and how you fixed it.   :)

---

### Post by kansasnoob on 2010-12-18
> **Herman said:**
> :D @ kansasnoob, thanks for your input. 

Maybe you missed something there, that experiment is about what happens when we install *all except the boot.img* of GRUB to the Windows partition.
It's not about what happens if we accidentally install the boot sector, which is what you seem to be on about, and that's a different subject for another experiment later on maybe.

Unless you'd like to help by contributing an experiment of your own to prove what happens when GRUB is installed to the Windows boot sector if that's what you want to talk about. 
You might describe what error messages you see if any or what behavior you observed, and how you fixed it.   :)

I guess that's beyond my comprehension :D

What benefit does this provide?

Wherever possible I like to keep things simple.

---

### Post by Herman on 2010-12-18
> What benefit does this provide? > This may be useful to know because it has happened once that a user  accidentally install GRUB to their Windows 7 /boot partition in this  way, (I don't know how they could have managed to do that by accident,  but anyway), and did not need to re-install  Windows because of it,  which surprised some people. This might also be useful for someone with a   maximum number of partitions problem and wants to add a 'Dedicated  GRUB Partition but can't have any more partitions. GRUB installed in the  Windows 7 /boot partition this way could be used as a 'Dedicated GRUB  Partition'.GRUB comes in three parts, the boot.img which is install to MBR or to a boot sector, the core.img which is normally installed in the first track of a hard disk before the start of any file systems, (partitions), and the grub files which are in the /boot/grub directory in a file system.

The experiment in [post #2]("http://ubuntuforums.org/showpost.php?p=10252336&postcount=2")  **_was_** about what happens when we install the /boot/grub files inside the Windows partition, and the boot.img and core.img to the first hard disk (MBR).
It **_was not_** about installing boot.img to the Windows boot sector.

I am preparing to begin the other experiment for you about what happens when we install boot.img of GRUB to the Windows 7 boot sector and bork the boot of Windows 7 and I'll post that here sometime in the near future for you.  :grin:

---

### Post by oldfred on 2010-12-18
I do not have Windows 7 but just old XP. But I wanted to know a little about it and just to have an emergency Win7 repair tool.  I wanted to create a USB flash with the neosmart download.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

I tried all the ways of copying it to a USB flash that I could, directly from ISO with FAT or NTFS with boot flag, with unetbootin, but nothing worked. I ended up creating a CD and from its boot copied it to the flash with normal windows commands. But it only took up a small part of the USB flash drive. So I said what else can it do. And I had just created a grub2 loopmount multiple ISO flash drive.

Now to Herman's point.

I just installed grub2 to the flash drive. It was FAT32. I manually added a chainboot stanza to boot the win7 repair and it worked. I was actually surprised that it worked. 

I then shrank the win partition and added another partition with several ISOs and added them to grub.cfg. Now I have a multipurpose repair USB flash drive that can run chkdsk (the one thing we cannot run from Linux), windows repairs, or boot Linux and run other repairs.

---

### Post by Herman on 2010-12-18
:D That's ubber cool, oldfred, thank you for contributing your experiment to this thread! 
I might make myself one of those too! :)

---

### Post by Quackers on 2010-12-18
Very enlightening people :-)
I'm looking forward to the grub files in the boot sector of Win 7 experiment (and XP maybe?) :-)

---

### Post by Herman on 2010-12-19
> I'm looking forward to the grub files in the boot sector of Win 7 experiment (and XP maybe?) :smile:@ Quackers:  ROFL!

Okay, here it is:

**Aim:** To find out what happens when GRUB's boot.img is forced into  the boot sector of a Windows 7 installation, (what symptoms it produces  when attempting to boot Windows 7), and to find out how to recover  Windows 7 from the damaged boot sector.

**Method: **

1. First I ran meierfra's bootinfo script so you can see what everything was like before I started and here are the results,
Before: 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub in the file /feisty.img looks at sector 147846401 
                       of the same hard drive for the stage2 file, but no 
                       stage2 files can be found at this location. Grub in 
                       the file /gutsy.img looks at sector 141169135 of the 
                       same hard drive for the stage2 file, but no stage2 
                       files can be found at this location.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg /boot/grub/core.img

sde1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   125,038,591   125,036,544  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   317,673,471   317,466,624   7 HPFS/NTFS
/dev/sdb3         317,673,472   625,141,759   307,468,288   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,547,300,474 1,547,300,412  83 Linux
/dev/sdc2       1,750,346,010 1,953,520,064   203,174,055  83 Linux
/dev/sdc3       1,547,300,475 1,750,346,009   203,045,535  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 514 MB, 514850816 bytes
255 heads, 63 sectors/track, 62 cylinders, total 1005568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63       996,029       995,967  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 16.0 GB, 16028532736 bytes
82 heads, 18 sectors/track, 21209 cylinders, total 31305728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          6,272    31,305,727    31,299,456  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        97f5afde-c174-4c1d-8814-a0b495059d3f   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7A08DC2308DBDC67                       ntfs       System_Reserved               
/dev/sdb2        5462DF4462DF298E                       ntfs                                     
/dev/sdb3        0B7124E350D25984                       ntfs       WINDOWS_XP                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        fc157c58-069e-4d1b-9613-e4843067f785   ext4       DATA_1000GB                   
/dev/sdc2        eb783d62-e1eb-4f3c-8931-84211444206c   ext4       OCZ_SAVER                     
/dev/sdc3        cb4e08c2-01b9-4ce6-b6d6-213bd52f8332   ext4       OCZ_SAVER_II                  
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        a678a230-d764-46f5-b9f3-55be5c1fd207   reiserfs   WEBSITE                       
/dev/sdd: PTTYPE="dos" 
/dev/sde1        443e8101-22cf-4bea-84c6-56f857d29caf   ext4       KINGSTON-KARMIC               
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,noatime,errors=remount-ro)
/dev/sde1        /media/KINGSTON-KARMIC   ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /media/WEBSITE           reiserfs   (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1600x1200
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward ***patibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
insmod play
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
insmod jpeg
if background_image /usr/share/images/grub/episteme1680.jpg ; then
  set color_normal=light-red/black
  set color_highlight=yellow/red
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/22_invaders ###
menuentry "GRUB Invaders" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    multiboot    /boot/invaders.exec
}
### END /etc/grub.d/22_invaders ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 7a08dc2308dbdc67
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this ***ment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=97f5afde-c174-4c1d-8814-a0b495059d3f /               ext4    noatime,errors=remount-ro 0       1
/swapfile         none         swap       sw          0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  60.2GB: boot/grub/core.img
  26.1GB: boot/grub/grub.cfg
  60.4GB: boot/initrd.img-2.6.32-21-generic
  60.4GB: boot/initrd.img-2.6.32-22-generic
  60.4GB: boot/initrd.img-2.6.32-23-generic
  60.5GB: boot/initrd.img-2.6.32-24-generic
  11.5GB: boot/initrd.img-2.6.32-25-generic
  14.5GB: boot/initrd.img-2.6.32-26-generic
  60.2GB: boot/vmlinuz-2.6.32-21-generic
  24.2GB: boot/vmlinuz-2.6.32-22-generic
  26.7GB: boot/vmlinuz-2.6.32-23-generic
  60.4GB: boot/vmlinuz-2.6.32-24-generic
  60.4GB: boot/vmlinuz-2.6.32-25-generic
  60.5GB: boot/vmlinuz-2.6.32-26-generic
  14.5GB: initrd.img
  11.5GB: initrd.img.old
  60.5GB: vmlinuz
  60.4GB: vmlinuz.old

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sdd1/boot/grub/grub.cfg: ===========================

#
# Sample GRUB configuration file
#

insmod biosdisk
insmod pc
insmod gpt

# Boot automatically after 30 secs.
set timeout=30

# By default, boot the first entry.
set default=0

# Fallback to the second entry.
set fallback=1

# For booting GNU/Hurd
menuentry "GNU (aka GNU/Hurd)" {
    set root=(hd0,1)
    multiboot /boot/gnumach.gz root=device:hd0s1
    module /hurd/ext2fs.static --readonly \
            --multiboot-***mand-line='${kernel-***mand-line}' \
            --host-priv-port='${host-port}' \
            --device-master-port='${device-port}' \
            --exec-server-task='${exec-task}' -T typed '${root}' \
            '$(task-create)' '$(task-resume)'
    module /lib/ld.so.1 /hurd/exec '$(exec-task=task-create)'
}

# For booting GNU/Linux
menuentry "GNU/Linux" {
    set root=(hd0,1)
    linux /vmlinuz root=/dev/sda1
    initrd /initrd.img
}

# For booting FreeBSD
menuentry "FreeBSD (or GNU/kFreeBSD), direct boot" {
    set root=(hd0,1,a)
    freebsd /boot/kernel/kernel
    freebsd_loadenv /boot/device.hints
    freebsd_module /boot/splash.bmp type=splash_image_data
    set FreeBSD.vfs.root.mountfrom=ufs:ad0s1a
}
menuentry "FreeBSD (or GNU/kFreeBSD), via /boot/loader" {
    set root=(hd0,1,a)
    freebsd /boot/loader
}

# For booting NetBSD
menuentry "NetBSD" {
    set root=(hd0,1,a)
    netbsd /netbsd
}

# For booting OpenBSD
menuentry "OpenBSD" {
    set root=(hd0,1,a)
    openbsd /bsd
}

# For booting Microsoft Windows
menuentry "Microsoft Windows" {
    set root=(hd0,1)
    chainloader +1
}

# For booting Memtest86+
menuentry "Memtest86+" {
    set root=(hd0,1)
    linux16 /memtest86+.bin
}

# Change the colors.
menuentry "Change the colors" {
    set menu_color_normal=light-green/brown
    set menu_color_highlight=red/blue
}

=================== sdd1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg

=========================== sde1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward ***patibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-20-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-17-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro elevator=noop  quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro single elevator=noop
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a08dc2308dbdc67
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this ***ment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=443e8101-22cf-4bea-84c6-56f857d29caf /               ext4    noatime,errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/swapfile          none         swap       sw           0       0

=================== sde1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   9.8GB: boot/grub/grub.cfg
   6.0GB: boot/initrd.img-2.6.31-17-generic
   7.2GB: boot/initrd.img-2.6.31-17-generic-pae
   9.0GB: boot/initrd.img-2.6.31-20-generic
  12.4GB: boot/initrd.img-2.6.31-20-generic-pae
  13.6GB: boot/initrd.img-2.6.32-22-generic
   6.9GB: boot/initrd.img-2.6.32-22-generic-pae
  14.4GB: boot/initrd.img-2.6.32-23-generic
   7.8GB: boot/initrd.img-2.6.32-23-generic-pae
  10.4GB: boot/initrd.img-2.6.32-24-generic
  10.5GB: boot/initrd.img-2.6.32-24-generic-pae
  11.1GB: boot/initrd.img-2.6.32-25-generic
  10.3GB: boot/initrd.img-2.6.32-25-generic-pae
   2.0GB: boot/vmlinuz-2.6.31-14-generic
   7.4GB: boot/vmlinuz-2.6.31-17-generic
   2.6GB: boot/vmlinuz-2.6.31-17-generic-pae
   8.0GB: boot/vmlinuz-2.6.31-20-generic
   8.0GB: boot/vmlinuz-2.6.31-20-generic-pae
   9.5GB: boot/vmlinuz-2.6.32-22-generic
  12.6GB: boot/vmlinuz-2.6.32-22-generic-pae
  13.7GB: boot/vmlinuz-2.6.32-23-generic
  13.7GB: boot/vmlinuz-2.6.32-23-generic-pae
   8.1GB: boot/vmlinuz-2.6.32-24-generic
   8.0GB: boot/vmlinuz-2.6.32-24-generic-pae
  10.5GB: boot/vmlinuz-2.6.32-25-generic
   4.4GB: boot/vmlinuz-2.6.32-25-generic-pae
  10.3GB: initrd.img
  11.1GB: initrd.img.old
   4.4GB: vmlinuz
  10.5GB: vmlinuz.old
```2. Secondly, I ran 'sudo blkid' to check and  confirm that my Windows 7  /boot partition is indeed in my second hard  disk and it's the first partition, so it's /dev/sdb1,
```
sudo blkid
/dev/sda1: UUID="97f5afde-c174-4c1d-8814-a0b495059d3f" TYPE="ext4" 
[COLOR=Blue]**/dev/sdb1: LABEL="System_Reserved" UUID="7A08DC2308DBDC67" TYPE="ntfs" **[/COLOR]
/dev/sdb2: UUID="5462DF4462DF298E" TYPE="ntfs" 
/dev/sdb3: LABEL="WINDOWS_XP" UUID="0B7124E350D25984" TYPE="ntfs" 
/dev/sdc1: LABEL="DATA_1000GB" UUID="fc157c58-069e-4d1b-9613-e4843067f785" TYPE="ext4" 
/dev/sdc2: LABEL="OCZ_SAVER" UUID="eb783d62-e1eb-4f3c-8931-84211444206c" TYPE="ext4" 
/dev/sdc3: LABEL="OCZ_SAVER_II" UUID="cb4e08c2-01b9-4ce6-b6d6-213bd52f8332" TYPE="ext4" 
/dev/sde1: LABEL="KINGSTON-KARMIC" UUID="443e8101-22cf-4bea-84c6-56f857d29caf" TYPE="ext4" 
/dev/sdd1: LABEL="WEBSITE" UUID="a678a230-d764-46f5-b9f3-55be5c1fd207"  TYPE="reiserfs" 
```3. I used a dd ***mand to make a backup copy of  the boot sector I'm about to trash just in case it turns out that I  can't fix it any other way. It will save me the time of re-installing  Windows 7 if that happens because I still want to be able to run a few  more experiments on it and trash it a few more times before I'm done  with it. :evil:
```
sudo dd if=/dev/sda1 of=/home/ubuntu/bootsector.img bs=512  count=1
```4. I ran 'sudo grub-install /dev/sdb1' to try to install  GRUB's boot.img to the second hard disk's first partition boot sector,
```
sudo grub-install /dev/sdb1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be  installed in this setup by using blocklists.  However, blocklists are  UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

```Okay, tough guy eh? Want me to force you then? Get ready because here goes,
```
sudo grub-install --force /dev/sdb1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be  installed in this setup by using blocklists.  However, blocklists are  UNRELIABLE and its use is discouraged..
Installation finished. No error reported.
```That did it! :twisted:

5. I rebooted and tried to boot Windows 7 like I normally can from GRUB  in Ubuntu in my first hard disk, (or should I say SSD), and try as I  might, all I was able to get was a black screen with a blinking cursor  in the upper left-hand corner every time I tried to boot Windows 7.

6. I booted my Windows7 Installation DVD to a repair console but was  shocked to see that my precious Windows7 installation was not even  detected! :-({|=

7. I opened the Windows ***mand Prompt instead and tried to run 'bootrec  /fixboot', but it gave me an error message and didn't work, so I tried  'bootrec fixboot C:' and it gave me another error message, something  about 'no such partition' or something. I tried 'bootrec /fixboot D:',  but that didn't appear to work either. 

Looks like I'm hosed. :shock:


=======================================


:-k  Well I could resort to using the dd backup I made of the Windows boot  sector, but that wouldn't satisfy my purpose for running this  experiment. Most new Windows users don't know how to make a dd backup of  their boot sector, they only turn up here ino this forum for help after  the damage has been done and it's too late.

:idea: Hey wait a minute, what if I unplug my first hard drive, (SSD), so Windows will be in the first hard drive?

==========================================

8. I rebooted into Ubuntu and ran meiefra's boot info script, (I almost  forgot to until now), here are the results with Windows 7 trashed,
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 117719872 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub in the file /feisty.img looks at sector 147846401 
                       of the same hard drive for the stage2 file, but no 
                       stage2 files can be found at this location. Grub in 
                       the file /gutsy.img looks at sector 141169135 of the 
                       same hard drive for the stage2 file, but no stage2 
                       files can be found at this location.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg /boot/grub/core.img

sde1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   125,038,591   125,036,544  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   317,673,471   317,466,624   7 HPFS/NTFS
/dev/sdb3         317,673,472   625,141,759   307,468,288   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,547,300,474 1,547,300,412  83 Linux
/dev/sdc2       1,750,346,010 1,953,520,064   203,174,055  83 Linux
/dev/sdc3       1,547,300,475 1,750,346,009   203,045,535  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 514 MB, 514850816 bytes
255 heads, 63 sectors/track, 62 cylinders, total 1005568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63       996,029       995,967  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 16.0 GB, 16028532736 bytes
82 heads, 18 sectors/track, 21209 cylinders, total 31305728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          6,272    31,305,727    31,299,456  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        97f5afde-c174-4c1d-8814-a0b495059d3f   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7A08DC2308DBDC67                       ntfs       System_Reserved               
/dev/sdb2        5462DF4462DF298E                       ntfs                                     
/dev/sdb3        0B7124E350D25984                       ntfs       WINDOWS_XP                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        fc157c58-069e-4d1b-9613-e4843067f785   ext4       DATA_1000GB                   
/dev/sdc2        eb783d62-e1eb-4f3c-8931-84211444206c   ext4       OCZ_SAVER                     
/dev/sdc3        cb4e08c2-01b9-4ce6-b6d6-213bd52f8332   ext4       OCZ_SAVER_II                  
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        a678a230-d764-46f5-b9f3-55be5c1fd207   reiserfs   WEBSITE                       
/dev/sdd: PTTYPE="dos" 
/dev/sde1        443e8101-22cf-4bea-84c6-56f857d29caf   ext4       KINGSTON-KARMIC               
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,noatime,errors=remount-ro)
/dev/sde1        /media/KINGSTON-KARMIC   ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /media/WEBSITE           reiserfs   (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1600x1200
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward ***patibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
insmod play
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
insmod jpeg
if background_image /usr/share/images/grub/episteme1680.jpg ; then
  set color_normal=light-red/black
  set color_highlight=yellow/red
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/22_invaders ###
menuentry "GRUB Invaders" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    multiboot    /boot/invaders.exec
}
### END /etc/grub.d/22_invaders ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 7a08dc2308dbdc67
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this ***ment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=97f5afde-c174-4c1d-8814-a0b495059d3f /               ext4    noatime,errors=remount-ro 0       1
/swapfile         none         swap       sw          0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  60.2GB: boot/grub/core.img
  26.1GB: boot/grub/grub.cfg
  60.4GB: boot/initrd.img-2.6.32-21-generic
  60.4GB: boot/initrd.img-2.6.32-22-generic
  60.4GB: boot/initrd.img-2.6.32-23-generic
  60.5GB: boot/initrd.img-2.6.32-24-generic
  11.5GB: boot/initrd.img-2.6.32-25-generic
  14.5GB: boot/initrd.img-2.6.32-26-generic
  60.2GB: boot/vmlinuz-2.6.32-21-generic
  24.2GB: boot/vmlinuz-2.6.32-22-generic
  26.7GB: boot/vmlinuz-2.6.32-23-generic
  60.4GB: boot/vmlinuz-2.6.32-24-generic
  60.4GB: boot/vmlinuz-2.6.32-25-generic
  60.5GB: boot/vmlinuz-2.6.32-26-generic
  14.5GB: initrd.img
  11.5GB: initrd.img.old
  60.5GB: vmlinuz
  60.4GB: vmlinuz.old

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sdd1/boot/grub/grub.cfg: ===========================

#
# Sample GRUB configuration file
#

insmod biosdisk
insmod pc
insmod gpt

# Boot automatically after 30 secs.
set timeout=30

# By default, boot the first entry.
set default=0

# Fallback to the second entry.
set fallback=1

# For booting GNU/Hurd
menuentry "GNU (aka GNU/Hurd)" {
    set root=(hd0,1)
    multiboot /boot/gnumach.gz root=device:hd0s1
    module /hurd/ext2fs.static --readonly \
            --multiboot-***mand-line='${kernel-***mand-line}' \
            --host-priv-port='${host-port}' \
            --device-master-port='${device-port}' \
            --exec-server-task='${exec-task}' -T typed '${root}' \
            '$(task-create)' '$(task-resume)'
    module /lib/ld.so.1 /hurd/exec '$(exec-task=task-create)'
}

# For booting GNU/Linux
menuentry "GNU/Linux" {
    set root=(hd0,1)
    linux /vmlinuz root=/dev/sda1
    initrd /initrd.img
}

# For booting FreeBSD
menuentry "FreeBSD (or GNU/kFreeBSD), direct boot" {
    set root=(hd0,1,a)
    freebsd /boot/kernel/kernel
    freebsd_loadenv /boot/device.hints
    freebsd_module /boot/splash.bmp type=splash_image_data
    set FreeBSD.vfs.root.mountfrom=ufs:ad0s1a
}
menuentry "FreeBSD (or GNU/kFreeBSD), via /boot/loader" {
    set root=(hd0,1,a)
    freebsd /boot/loader
}

# For booting NetBSD
menuentry "NetBSD" {
    set root=(hd0,1,a)
    netbsd /netbsd
}

# For booting OpenBSD
menuentry "OpenBSD" {
    set root=(hd0,1,a)
    openbsd /bsd
}

# For booting Microsoft Windows
menuentry "Microsoft Windows" {
    set root=(hd0,1)
    chainloader +1
}

# For booting Memtest86+
menuentry "Memtest86+" {
    set root=(hd0,1)
    linux16 /memtest86+.bin
}

# Change the colors.
menuentry "Change the colors" {
    set menu_color_normal=light-green/brown
    set menu_color_highlight=red/blue
}

=================== sdd1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg

=========================== sde1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward ***patibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-20-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-17-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro elevator=noop  quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro single elevator=noop
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a08dc2308dbdc67
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this ***ment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=443e8101-22cf-4bea-84c6-56f857d29caf /               ext4    noatime,errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/swapfile          none         swap       sw           0       0

=================== sde1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   9.8GB: boot/grub/grub.cfg
   6.0GB: boot/initrd.img-2.6.31-17-generic
   7.2GB: boot/initrd.img-2.6.31-17-generic-pae
   9.0GB: boot/initrd.img-2.6.31-20-generic
  12.4GB: boot/initrd.img-2.6.31-20-generic-pae
  13.6GB: boot/initrd.img-2.6.32-22-generic
   6.9GB: boot/initrd.img-2.6.32-22-generic-pae
  14.4GB: boot/initrd.img-2.6.32-23-generic
   7.8GB: boot/initrd.img-2.6.32-23-generic-pae
  10.4GB: boot/initrd.img-2.6.32-24-generic
  10.5GB: boot/initrd.img-2.6.32-24-generic-pae
  11.1GB: boot/initrd.img-2.6.32-25-generic
  10.3GB: boot/initrd.img-2.6.32-25-generic-pae
   2.0GB: boot/vmlinuz-2.6.31-14-generic
   7.4GB: boot/vmlinuz-2.6.31-17-generic
   2.6GB: boot/vmlinuz-2.6.31-17-generic-pae
   8.0GB: boot/vmlinuz-2.6.31-20-generic
   8.0GB: boot/vmlinuz-2.6.31-20-generic-pae
   9.5GB: boot/vmlinuz-2.6.32-22-generic
  12.6GB: boot/vmlinuz-2.6.32-22-generic-pae
  13.7GB: boot/vmlinuz-2.6.32-23-generic
  13.7GB: boot/vmlinuz-2.6.32-23-generic-pae
   8.1GB: boot/vmlinuz-2.6.32-24-generic
   8.0GB: boot/vmlinuz-2.6.32-24-generic-pae
  10.5GB: boot/vmlinuz-2.6.32-25-generic
   4.4GB: boot/vmlinuz-2.6.32-25-generic-pae
  10.3GB: initrd.img
  11.1GB: initrd.img.old
   4.4GB: vmlinuz
  10.5GB: vmlinuz.old
```So I did unplug my first hard drive, (SSD to  be more accurate), and I booted the Windows 7 Installation DVD Recovery  Console again and selected 'Repair my ***puter'.
It searched for Windows installations and this time it successfully recognised my Windows7 installation.
I opened the ***mand Prompt again.
I ran 'bootrec /fixboot'
The operation ***pleted successfully this time.

I rebooted.
Window7 booted right up as fresh as a daisy with no problems at all. \\:D/

**Conclusions:**
(a) It seems as if Windows7 needs to be in the first hard disk for Windows Repairs to work.
(b) As soon as you can get Windows Recovery tools to work properly, it's  not very difficult to recover from a trashed Windows boot sector.

Here's the final boot info results with Windows7 fixed,
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub in the file /feisty.img looks at sector 147846401 
                       of the same hard drive for the stage2 file, but no 
                       stage2 files can be found at this location. Grub in 
                       the file /gutsy.img looks at sector 141169135 of the 
                       same hard drive for the stage2 file, but no stage2 
                       files can be found at this location.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg /boot/grub/core.img

sde1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   125,038,591   125,036,544  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   317,673,471   317,466,624   7 HPFS/NTFS
/dev/sdb3         317,673,472   625,141,759   307,468,288   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,547,300,474 1,547,300,412  83 Linux
/dev/sdc2       1,750,346,010 1,953,520,064   203,174,055  83 Linux
/dev/sdc3       1,547,300,475 1,750,346,009   203,045,535  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 514 MB, 514850816 bytes
255 heads, 63 sectors/track, 62 cylinders, total 1005568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63       996,029       995,967  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 16.0 GB, 16028532736 bytes
82 heads, 18 sectors/track, 21209 cylinders, total 31305728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          6,272    31,305,727    31,299,456  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        97f5afde-c174-4c1d-8814-a0b495059d3f   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7A08DC2308DBDC67                       ntfs       System_Reserved               
/dev/sdb2        5462DF4462DF298E                       ntfs                                     
/dev/sdb3        0B7124E350D25984                       ntfs       WINDOWS_XP                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        fc157c58-069e-4d1b-9613-e4843067f785   ext4       DATA_1000GB                   
/dev/sdc2        eb783d62-e1eb-4f3c-8931-84211444206c   ext4       OCZ_SAVER                     
/dev/sdc3        cb4e08c2-01b9-4ce6-b6d6-213bd52f8332   ext4       OCZ_SAVER_II                  
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        a678a230-d764-46f5-b9f3-55be5c1fd207   reiserfs   WEBSITE                       
/dev/sdd: PTTYPE="dos" 
/dev/sde1        443e8101-22cf-4bea-84c6-56f857d29caf   ext4       KINGSTON-KARMIC               
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,noatime,errors=remount-ro)
/dev/sde1        /media/KINGSTON-KARMIC   ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /media/WEBSITE           reiserfs   (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1600x1200
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward ***patibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
insmod play
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
insmod jpeg
if background_image /usr/share/images/grub/episteme1680.jpg ; then
  set color_normal=light-red/black
  set color_highlight=yellow/red
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro elevator=deadline  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=97f5afde-c174-4c1d-8814-a0b495059d3f ro single elevator=deadline
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/22_invaders ###
menuentry "GRUB Invaders" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 97f5afde-c174-4c1d-8814-a0b495059d3f
    multiboot    /boot/invaders.exec
}
### END /etc/grub.d/22_invaders ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 7a08dc2308dbdc67
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this ***ment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=97f5afde-c174-4c1d-8814-a0b495059d3f /               ext4    noatime,errors=remount-ro 0       1
/swapfile         none         swap       sw          0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  60.2GB: boot/grub/core.img
  26.1GB: boot/grub/grub.cfg
  60.4GB: boot/initrd.img-2.6.32-21-generic
  60.4GB: boot/initrd.img-2.6.32-22-generic
  60.4GB: boot/initrd.img-2.6.32-23-generic
  60.5GB: boot/initrd.img-2.6.32-24-generic
  11.5GB: boot/initrd.img-2.6.32-25-generic
  14.5GB: boot/initrd.img-2.6.32-26-generic
  60.2GB: boot/vmlinuz-2.6.32-21-generic
  24.2GB: boot/vmlinuz-2.6.32-22-generic
  26.7GB: boot/vmlinuz-2.6.32-23-generic
  60.4GB: boot/vmlinuz-2.6.32-24-generic
  60.4GB: boot/vmlinuz-2.6.32-25-generic
  60.5GB: boot/vmlinuz-2.6.32-26-generic
  14.5GB: initrd.img
  11.5GB: initrd.img.old
  60.5GB: vmlinuz
  60.4GB: vmlinuz.old

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sdd1/boot/grub/grub.cfg: ===========================

#
# Sample GRUB configuration file
#

insmod biosdisk
insmod pc
insmod gpt

# Boot automatically after 30 secs.
set timeout=30

# By default, boot the first entry.
set default=0

# Fallback to the second entry.
set fallback=1

# For booting GNU/Hurd
menuentry "GNU (aka GNU/Hurd)" {
    set root=(hd0,1)
    multiboot /boot/gnumach.gz root=device:hd0s1
    module /hurd/ext2fs.static --readonly \
            --multiboot-***mand-line='${kernel-***mand-line}' \
            --host-priv-port='${host-port}' \
            --device-master-port='${device-port}' \
            --exec-server-task='${exec-task}' -T typed '${root}' \
            '$(task-create)' '$(task-resume)'
    module /lib/ld.so.1 /hurd/exec '$(exec-task=task-create)'
}

# For booting GNU/Linux
menuentry "GNU/Linux" {
    set root=(hd0,1)
    linux /vmlinuz root=/dev/sda1
    initrd /initrd.img
}

# For booting FreeBSD
menuentry "FreeBSD (or GNU/kFreeBSD), direct boot" {
    set root=(hd0,1,a)
    freebsd /boot/kernel/kernel
    freebsd_loadenv /boot/device.hints
    freebsd_module /boot/splash.bmp type=splash_image_data
    set FreeBSD.vfs.root.mountfrom=ufs:ad0s1a
}
menuentry "FreeBSD (or GNU/kFreeBSD), via /boot/loader" {
    set root=(hd0,1,a)
    freebsd /boot/loader
}

# For booting NetBSD
menuentry "NetBSD" {
    set root=(hd0,1,a)
    netbsd /netbsd
}

# For booting OpenBSD
menuentry "OpenBSD" {
    set root=(hd0,1,a)
    openbsd /bsd
}

# For booting Microsoft Windows
menuentry "Microsoft Windows" {
    set root=(hd0,1)
    chainloader +1
}

# For booting Memtest86+
menuentry "Memtest86+" {
    set root=(hd0,1)
    linux16 /memtest86+.bin
}

# Change the colors.
menuentry "Change the colors" {
    set menu_color_normal=light-green/brown
    set menu_color_highlight=red/blue
}

=================== sdd1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg

=========================== sde1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward ***patibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-20-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-17-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro elevator=noop  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=443e8101-22cf-4bea-84c6-56f857d29caf ro single elevator=noop
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro elevator=noop  quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro single elevator=noop
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 443e8101-22cf-4bea-84c6-56f857d29caf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a08dc2308dbdc67
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this ***ment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=443e8101-22cf-4bea-84c6-56f857d29caf /               ext4    noatime,errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/swapfile          none         swap       sw           0       0

=================== sde1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   9.8GB: boot/grub/grub.cfg
   6.0GB: boot/initrd.img-2.6.31-17-generic
   7.2GB: boot/initrd.img-2.6.31-17-generic-pae
   9.0GB: boot/initrd.img-2.6.31-20-generic
  12.4GB: boot/initrd.img-2.6.31-20-generic-pae
  13.6GB: boot/initrd.img-2.6.32-22-generic
   6.9GB: boot/initrd.img-2.6.32-22-generic-pae
  14.4GB: boot/initrd.img-2.6.32-23-generic
   7.8GB: boot/initrd.img-2.6.32-23-generic-pae
  10.4GB: boot/initrd.img-2.6.32-24-generic
  10.5GB: boot/initrd.img-2.6.32-24-generic-pae
  11.1GB: boot/initrd.img-2.6.32-25-generic
  10.3GB: boot/initrd.img-2.6.32-25-generic-pae
   2.0GB: boot/vmlinuz-2.6.31-14-generic
   7.4GB: boot/vmlinuz-2.6.31-17-generic
   2.6GB: boot/vmlinuz-2.6.31-17-generic-pae
   8.0GB: boot/vmlinuz-2.6.31-20-generic
   8.0GB: boot/vmlinuz-2.6.31-20-generic-pae
   9.5GB: boot/vmlinuz-2.6.32-22-generic
  12.6GB: boot/vmlinuz-2.6.32-22-generic-pae
  13.7GB: boot/vmlinuz-2.6.32-23-generic
  13.7GB: boot/vmlinuz-2.6.32-23-generic-pae
   8.1GB: boot/vmlinuz-2.6.32-24-generic
   8.0GB: boot/vmlinuz-2.6.32-24-generic-pae
  10.5GB: boot/vmlinuz-2.6.32-25-generic
   4.4GB: boot/vmlinuz-2.6.32-25-generic-pae
  10.3GB: initrd.img
  11.1GB: initrd.img.old
   4.4GB: vmlinuz
  10.5GB: vmlinuz.old 
```

---

### Post by Quackers on 2010-12-19
Excellent :-)
That is enlightening :-) 
I'm wondering if making sdb1 the active partition with diskpart could have forced the startup repair to look there. What do you think Herman?
Thanks for that :-)

I've also got another one for you :-)
Sometimes we are seeing grldr as a third file in with the /bootmgr /boot/BCD files and it seems to stop Win 7 from booting. Is this likely to be caused by grldr over-writing one of the files or just because it's there?

---

### Post by Herman on 2010-12-19
> I'm wondering if making sdb1 the active partition with diskpart could  have forced the startup repair to look there. What do you think Herman? Referring to the results from the bootinfo script, you should be able to see that the Windows 7 /boot partition *did* have the boot flag, but when my Ubuntu SSD is plugged in as first hard disk, the Windows7 disk is not the first hard disk. I am only guessing, but I think probably the Windows Repair DVD assumes Windows will be in the first hard disk and isn't programmed to deal with any other situation. At least that's how things seem to me.
> I've also got another one for you :smile:
Sometimes we are seeing grldr as a third file in with the /bootmgr  /boot/BCD files and it seems to stop Win 7 from booting. Is this likely  to be caused by grldr over-writing one of the files or just because it's  there? 	Yeah, I was already thinking about trying a wubi install, I've never tried one of those. First I need to read Rubi1200's  [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198") again though.  It looks like some of the answers people might have about wubi's effects on booting Windows are already described there. I'll haven't yet quite decided what exactly what kind of experiment I should do with wubi.

---

### Post by Quackers on 2010-12-19
Yes, I noticed the correct boot flag on sdb1. I was wondering if startup repair could be forced to look anywhere. I suspect not. It seems that Windows is back to thinking it is the only OS that can occupy a disc and, as such, will always be at the start of the first hard drive.

On the second point, I wsn't thinking of wubi. 
It seems that when some people have grub problems they look on the net and find a guide for re-installing grub. Often it is the case that they follow an older guide which refers to grub legacy. I was assuming that this is how they get grldr in with the Windows boot files. But I could be wrong :-)

---

### Post by Herman on 2010-12-19
GRLDR isn't part of Legacy GRUB. 
I have a web page about WinGRUB here, [WinGRUB Page]("http://members.iinet.net.au/%7Eherman546/p9.html"), and I know that GRLDR is part of WinGRUB.
I have read that wubi uses WinGrub for booting with, but I have no idea how that works. 

Okay, I'll just perform a wubi installation in Windows7 and then I'll run the bootinfo script again and see if GRLDR turns up in my Windows7 files.

---

### Post by Quackers on 2010-12-19
Ah I see! I made the wrong assumption! Not for the first time :-) So it gets there through a wubi installation. Thanks for that correction. 
I think this thread will teach me a lot :-)

---

### Post by Herman on 2010-12-19
Copying Windows XP to a Non-First Partition.

**Aim:**
The aim of this experiment is to copy Windows XP to a non-first partition and boot.

[B]What I am expecting to happen: 
[/B]I have performed similar experiments before, and usually Windows XP will not be bootable and display an error message like '[hal.dll is missing or corrupt]("http://members.iinet.net.au/%7Eherman546/p15.html#hal.dll_is_missing_or_corrupt")' or '[NTLDR is missing, press any key to restart]("http://members.iinet.net.au/%7Eherman546/p15.html#NTLDR_is_missing_press_any_key_to")'.
It is then usually necessary to edit the boot.ini file in Windows XP to tell it it's now in a different partition number.
An easier way to fix boot.ini is to boot to an Windows XP [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and run 'bootcfg /rebuild', and that will generate a new boot.ini file.

**Method:**

1. I booted up my lates copy of Parted Magic Live CD, which is version 5.7 and I used it to copy and paste my Windows XP file system to another partition, which became partition number 2 in the first hard disk.

2. I used GParted and the Parted Magic 5.7 Live CD to delete my original copy of Windows XP in partition number 1 of the first hard disk.

3. I rebooted and selected Windows XP from my GRUB Menu.

**Result:**
Windows XP booted right up without any problem. 


:confused: Now that has me puzzled. Is it improvements in GRUB over Legacy GRUB that help Windows XP to be able to boot in the different partition number or is it something in Parted Magic's advanced version of GParted?

BootInfo Results text before:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /grub/menu.lst /boot.ini /grldr /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    40,962,047    40,960,000   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    74,272,768    74,270,721  83 Linux
/dev/sdb2         130,756,606   156,301,311    25,544,706   5 Extended
/dev/sdb5         150,290,432   156,301,311     6,010,880  82 Linux swap / Solaris
/dev/sdb6         130,756,608   150,288,383    19,531,776  83 Linux
/dev/sdb3          74,274,816   130,754,559    56,479,744  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2629-16F0                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        af1b759b-dcb1-4579-b9f6-0da6d3e23eb2   ext4       LYNX                          
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        ec345b87-039c-4bb8-901d-d08acc968cd6   ext4                                     
/dev/sdb5        af407266-0dff-4698-9fc5-9f3b764bd0f3   swap                                     
/dev/sdb6        6655ee5e-45d1-4d1c-9a7d-10f30f16e745   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


============================= sda1/grub/menu.lst: =============================

timeout 10 
 
title Windows at (hd0,0) 
root (hd0,0) 
chainloader +1
================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /FASTDETECT /NOEXECUTE=OPTIN 
c:\GRLDR="Start Grub"  

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: grub/menu.lst

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2629-16f0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdb3)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdb3)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb3)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb3)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb6)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb6)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb6)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb6)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=af407266-0dff-4698-9fc5-9f3b764bd0f3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
   6.8GB: boot/grub/grub.cfg
  21.6GB: boot/initrd.img-2.6.32-21-generic
  21.7GB: boot/initrd.img-2.6.32-25-generic
  22.0GB: boot/initrd.img-2.6.32-26-generic
  21.6GB: boot/vmlinuz-2.6.32-21-generic
  21.7GB: boot/vmlinuz-2.6.32-25-generic
  21.9GB: boot/vmlinuz-2.6.32-26-generic
  22.0GB: initrd.img
  21.7GB: initrd.img.old
  21.9GB: vmlinuz
  21.7GB: vmlinuz.old

=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
insmod play
play 480 900 2 1000 2 800 2 400 2 600 3
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=red/yellow
set menu_color_highlight=light-magenta/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2629-16f0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=af407266-0dff-4698-9fc5-9f3b764bd0f3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  69.3GB: boot/grub/core.img
  73.8GB: boot/grub/grub.cfg
  70.4GB: boot/initrd.img-2.6.32-21-generic
  75.1GB: boot/initrd.img-2.6.32-24-generic
  70.3GB: boot/vmlinuz-2.6.32-21-generic
  74.7GB: boot/vmlinuz-2.6.32-24-generic
  75.1GB: initrd.img
  70.4GB: initrd.img.old
  74.7GB: vmlinuz
  70.3GB: vmlinuz.old

=========================== sdb3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2629-16f0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=af407266-0dff-4698-9fc5-9f3b764bd0f3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


  57.4GB: boot/grub/core.img
  57.5GB: boot/grub/grub.cfg
  38.5GB: boot/initrd.img-2.6.35-22-generic
  40.8GB: boot/initrd.img-2.6.35-23-generic
  57.4GB: boot/vmlinuz-2.6.35-22-generic
  57.5GB: boot/vmlinuz-2.6.35-23-generic
  40.8GB: initrd.img
  38.5GB: initrd.img.old
  57.5GB: vmlinuz
  57.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  ec 5c 8b 5d 08 85 db 27  b2 65 c5 63 50 25 5f 16  |.\.]...'.e.cP%_.|
00000010  d3 8b 8a 22 68 32 a3 11  8b 52 7c ac 11 03 c1 73  |..."h2...R|....s|
00000020  39 8b bb 98 4c ba 00 04  8d 0c 8a 89 4d b4 85 ff  |9...L.......M...|
00000030  74 0f 8d 47 08 39 47 08  89 45 b0 0f 85 05 71 d2  |t..G.9G..E....q.|
00000040  55 12 b5 19 0b 22 04 ac  4a 1e f7 60 42 dd 65 f4  |U...."..J..`B.e.|
00000050  98 22 50 22 25 d6 b7 8b  b8 68 08 01 85 ff 74 d2  |."P"%....h....t.|
00000060  26 87 b3 b8 74 c7 29 f8  b2 22 16 fc e8 80 22 74  |&...t.).."...."t|
00000070  27 03 4d b8 8d 45 c4 89  22 66 5f 04 24 13 94 09  |'.M..E.."f_.$...|
00000080  03 4c 24 04 e8 82 f9 23  cf 25 8b 75 c4 6a 1c 48  |.L$....#.%.u.j.H|
00000090  06 40 16 07 45 b8 8b 18  39 f3 75 08 eb 2c 23 fb  |.@..E...9.u..,#.|
000000a0  b2 26 8b 53 74 10 05 f3  8b 4a 04 85 c9 74 ec 23  |.&.St....J...t.#|
000000b0  f9 b2 e6 fc b3 01 14 24  ff d1 77 04 75 da 8b 78  |.......$..w.u..x|
000000c0  0b 01 bc 89 75 dc 22 88  af 22 dc b2 77 0b a4 f9  |....u.".."..w...|
000000d0  ec 2e df b2 0f 84 e6 49  1e 0f 2b 8e b1 0f 85 22  |.......I..+...."|
000000e0  10 3c 04 80 7f 04 00 0f  84 08 44 5f 22 5d 3d 5d  |.<........D_"]=]|
000000f0  22 78 3b 01 fb fe ff ff  29 2c 03 23 35 8a b4 22  |"x;.....),.#5.."|
00000100  c0 3d 01 55 b0 8d 45 12  95 03 0c 64 0d 22 a0 62  |.=.U..E....d.".b|
00000110  12 56 04 b6 f8 cc 19 23  ee 8f 7c 05 4c 19 01 4d  |.V.....#..|.L..M|
00000120  b0 8b 19 8d 19 2e 76 14  74 28 94 64 08 66 90 74  |......v.t(.d.f.t|
00000130  f1 8b 50 04 85 d2 74 ea  97 19 e4 8b 4d 22 29 8a  |..P...t.....M").|
00000140  89 12 e5 37 d2 7f 04 75  d8 8b 61 0c c8 29 34 03  |...7...u..a..)4.|
00000150  7e 0b d6 f8 30 36 03 85  32 9d cb b0 74 27 01 f6  |~...06..2...t'..|
00000160  f7 ec ff 69 17 62 22 41  28 40 5b c6 8b 45 b8 22  |...i.b"A(@[..E."|
00000170  00 51 07 de f7 ec ff eb  e6 89 45 ac 0f 2a 9e b5  |.Q........E..*..|
00000180  3b 0f 2b 0d 04 75 29 9d  b5 61 22 f4 30 03 4d 08  |;.+..u)..a".0.M.|
00000190  85 c9 74 0b 22 68 20 02  14 24 e8 fb 5e 71 19 ac  |..t."h ..$..^q..|
000001a0  22 5d eb 44 7e 1f 5d b8  61 0e 85 c2 0e f1 0f 40  |"].D~.].a......@|
000001b0  0c 07 ce 8b 55 b8 89 45  ac 8d 45 c0 f8 16 00 fe  |....U..E..E.....|
000001c0  ff ff 82 fe ff ff 02 10  2a 01 00 b8 5b 00 00 fe  |........*...[...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 08 2a 01 00 00  |............*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```Bootinfo Results text after:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /grub/menu.lst /boot.ini /grldr /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2          40,962,048    81,922,047    40,960,000   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    74,272,768    74,270,721  83 Linux
/dev/sdb2         130,756,606   156,301,311    25,544,706   5 Extended
/dev/sdb5         150,290,432   156,301,311     6,010,880  82 Linux swap / Solaris
/dev/sdb6         130,756,608   150,288,383    19,531,776  83 Linux
/dev/sdb3          74,274,816   130,754,559    56,479,744  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        2629-16F0                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        af1b759b-dcb1-4579-b9f6-0da6d3e23eb2   ext4       LYNX                          
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        ec345b87-039c-4bb8-901d-d08acc968cd6   ext4                                     
/dev/sdb5        af407266-0dff-4698-9fc5-9f3b764bd0f3   swap                                     
/dev/sdb6        6655ee5e-45d1-4d1c-9a7d-10f30f16e745   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb3        /media/ec345b87-039c-4bb8-901d-d08acc968cd6 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/2629-16F0         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


============================= sda2/grub/menu.lst: =============================

timeout 10 
 
title Windows at (hd0,0) 
root (hd0,0) 
chainloader +1
================================ sda2/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /FASTDETECT /NOEXECUTE=OPTIN 
c:\GRLDR="Start Grub"  

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: grub/menu.lst

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2629-16f0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdb3)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdb3)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb3)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb3)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb6)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb6)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb6)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb6)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=af407266-0dff-4698-9fc5-9f3b764bd0f3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
   6.8GB: boot/grub/grub.cfg
  21.6GB: boot/initrd.img-2.6.32-21-generic
  21.7GB: boot/initrd.img-2.6.32-25-generic
  22.0GB: boot/initrd.img-2.6.32-26-generic
  21.6GB: boot/vmlinuz-2.6.32-21-generic
  21.7GB: boot/vmlinuz-2.6.32-25-generic
  21.9GB: boot/vmlinuz-2.6.32-26-generic
  22.0GB: initrd.img
  21.7GB: initrd.img.old
  21.9GB: vmlinuz
  21.7GB: vmlinuz.old

=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
insmod play
play 480 900 2 1000 2 800 2 400 2 600 3
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=red/yellow
set menu_color_highlight=light-magenta/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2629-16f0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=af407266-0dff-4698-9fc5-9f3b764bd0f3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  69.3GB: boot/grub/core.img
  73.8GB: boot/grub/grub.cfg
  70.4GB: boot/initrd.img-2.6.32-21-generic
  75.1GB: boot/initrd.img-2.6.32-24-generic
  70.3GB: boot/vmlinuz-2.6.32-21-generic
  74.7GB: boot/vmlinuz-2.6.32-24-generic
  75.1GB: initrd.img
  70.4GB: initrd.img.old
  74.7GB: vmlinuz
  70.3GB: vmlinuz.old

=========================== sdb3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2629-16f0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set af1b759b-dcb1-4579-b9f6-0da6d3e23eb2
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=af1b759b-dcb1-4579-b9f6-0da6d3e23eb2 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=af407266-0dff-4698-9fc5-9f3b764bd0f3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


  57.4GB: boot/grub/core.img
  57.5GB: boot/grub/grub.cfg
  38.5GB: boot/initrd.img-2.6.35-22-generic
  40.8GB: boot/initrd.img-2.6.35-23-generic
  57.4GB: boot/vmlinuz-2.6.35-22-generic
  57.5GB: boot/vmlinuz-2.6.35-23-generic
  40.8GB: initrd.img
  38.5GB: initrd.img.old
  57.5GB: vmlinuz
  57.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  ec 5c 8b 5d 08 85 db 27  b2 65 c5 63 50 25 5f 16  |.\.]...'.e.cP%_.|
00000010  d3 8b 8a 22 68 32 a3 11  8b 52 7c ac 11 03 c1 73  |..."h2...R|....s|
00000020  39 8b bb 98 4c ba 00 04  8d 0c 8a 89 4d b4 85 ff  |9...L.......M...|
00000030  74 0f 8d 47 08 39 47 08  89 45 b0 0f 85 05 71 d2  |t..G.9G..E....q.|
00000040  55 12 b5 19 0b 22 04 ac  4a 1e f7 60 42 dd 65 f4  |U...."..J..`B.e.|
00000050  98 22 50 22 25 d6 b7 8b  b8 68 08 01 85 ff 74 d2  |."P"%....h....t.|
00000060  26 87 b3 b8 74 c7 29 f8  b2 22 16 fc e8 80 22 74  |&...t.).."...."t|
00000070  27 03 4d b8 8d 45 c4 89  22 66 5f 04 24 13 94 09  |'.M..E.."f_.$...|
00000080  03 4c 24 04 e8 82 f9 23  cf 25 8b 75 c4 6a 1c 48  |.L$....#.%.u.j.H|
00000090  06 40 16 07 45 b8 8b 18  39 f3 75 08 eb 2c 23 fb  |.@..E...9.u..,#.|
000000a0  b2 26 8b 53 74 10 05 f3  8b 4a 04 85 c9 74 ec 23  |.&.St....J...t.#|
000000b0  f9 b2 e6 fc b3 01 14 24  ff d1 77 04 75 da 8b 78  |.......$..w.u..x|
000000c0  0b 01 bc 89 75 dc 22 88  af 22 dc b2 77 0b a4 f9  |....u.".."..w...|
000000d0  ec 2e df b2 0f 84 e6 49  1e 0f 2b 8e b1 0f 85 22  |.......I..+...."|
000000e0  10 3c 04 80 7f 04 00 0f  84 08 44 5f 22 5d 3d 5d  |.<........D_"]=]|
000000f0  22 78 3b 01 fb fe ff ff  29 2c 03 23 35 8a b4 22  |"x;.....),.#5.."|
00000100  c0 3d 01 55 b0 8d 45 12  95 03 0c 64 0d 22 a0 62  |.=.U..E....d.".b|
00000110  12 56 04 b6 f8 cc 19 23  ee 8f 7c 05 4c 19 01 4d  |.V.....#..|.L..M|
00000120  b0 8b 19 8d 19 2e 76 14  74 28 94 64 08 66 90 74  |......v.t(.d.f.t|
00000130  f1 8b 50 04 85 d2 74 ea  97 19 e4 8b 4d 22 29 8a  |..P...t.....M").|
00000140  89 12 e5 37 d2 7f 04 75  d8 8b 61 0c c8 29 34 03  |...7...u..a..)4.|
00000150  7e 0b d6 f8 30 36 03 85  32 9d cb b0 74 27 01 f6  |~...06..2...t'..|
00000160  f7 ec ff 69 17 62 22 41  28 40 5b c6 8b 45 b8 22  |...i.b"A(@[..E."|
00000170  00 51 07 de f7 ec ff eb  e6 89 45 ac 0f 2a 9e b5  |.Q........E..*..|
00000180  3b 0f 2b 0d 04 75 29 9d  b5 61 22 f4 30 03 4d 08  |;.+..u)..a".0.M.|
00000190  85 c9 74 0b 22 68 20 02  14 24 e8 fb 5e 71 19 ac  |..t."h ..$..^q..|
000001a0  22 5d eb 44 7e 1f 5d b8  61 0e 85 c2 0e f1 0f 40  |"].D~.].a......@|
000001b0  0c 07 ce 8b 55 b8 89 45  ac 8d 45 c0 f8 16 00 fe  |....U..E..E.....|
000001c0  ff ff 82 fe ff ff 02 10  2a 01 00 b8 5b 00 00 fe  |........*...[...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 08 2a 01 00 00  |............*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```**Conclusions:**
It's too early to draw any conclusions from this unexpected result. I will need to repeat this experiment in a different computer to see if the same results can be repeated.

:idea: I'll try re-installing the Windows boot loader to MBR to see if I can get it to be unable to boot and produce the expected error messages, as a test to try to find out if it seems to be improvements in GRUB that cause this unexpectedly good result.

What the ...? 
I booted the Windows XP Recovery Console and ran fixmbr and fixboot just for good measure and it booted to 'DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER". Then I remembers I had forgotten to set the boot flag on the new partition. I used GParted in Parted Magic Live CD to do so, and Windows XP is able to boot okay by itself in /dev/sda2 without needing to edit boot.ini. 
Most peculiar. ????

---

### Post by owiknowi on 2010-12-19
herman (and others),

would it be useful for this experiment if i install grub to my ntfs windos7 partition (last part of hdd, sda9)?

btw. 1. i agree that you can install windos to other partitions.
however didn't know that earlier versions than ms titanic were able to do so as well.
knew no better than it had to be on the first primary (i stopped using it after w2k).

however installing windos last, it does mess up the partition table i experienced and it takes over the mbr.

! > of course the partition table looks different with this configuration:
sda1 (pri, ext4), sda2 (swap), sda3 (extended with logical partitions, all ext4) and sda4 (pri, ntfs, boot) added last makes the latter not sda9 but of course sda4.
sorry, my bad < !

btw. 2. i use to partition leaving some unallocated space before the first partition.
also i normally let the partitions round up to cylinders.
anyone any idea if this makes sense or even is useful?

btw. 3. what if i make no primary partition at all?
example: sda1 (linux swap), sda2 extended (with several logical volumes and one ntfs with boot flag)?

---

### Post by Herman on 2010-12-19
> would it be useful for this experiment if i install grub to my ntfs windos7 partition (last part of hdd, sda9)?No, I don't think that will be useful for you unless you're trying to do something special that I don't understand yet.
> btw. 1. i agree that you can install windos to other partitions.
however didn't know that earlier versions than ms titanic were able to do so as well.
knew no better than it had to be on the first primary (i stopped using it after w2k).Okay. A lot of other people do think that Windows needs to be in the first partition and located physically at the start of the hard disk and it has to be in a primary partition though. The idea of this thread is to try to prove whether some of the things many people believe and like to keep repeating actually have any factual basis.
> however installing windos last, it does mess up the partition table i experienced and it takes over the mbr.I know it takes over the MBR, but I didn't know it messes up the partition table, that's interesting. I'll do some work on that sometime and try to find out if that's reproduce-able. Unless you want to?
> btw. 2. i use to partition leaving some unallocated space before the first partition.
also i normally let the partitions round up to cylinders.
anyone any idea if this makes sense or even is useful?In an experiment I made in a different thread it didn't make any difference to Windows XP or Windows 98SE to have them aligned to the new MiB partition alignment trend. I think the new MiB alignment will be what we'll all be using in the future.
> btw. 3. what if i make no primary partition at all?
example: sda1 (linux swap), sda2 extended (with several logical volumes and one ntfs with boot flag)? 	It should work, I'm not sure, try it and let us know what happens. :)

---

### Post by Herman on 2010-12-19
**Aim: **
To see if Windows XP can be booted in a logical partition.

**Background:**
I have already proven this can be done but it was a while ago and I think the last time I used Legacy GRUB, (if I remember correctly),  and I'm trying it again to make sure it's still possible.

Following on from [post #19]("http://ubuntuforums.org/showpost.php?p=10255411&postcount=19"), when I had Windows XP booting in a non-first partition that was in the middle of the hard disk, I performed the following steps,

1. I booted Parted Magic 5.7 Live CD and 
(a) I created an empty new extended partition
(b) I copied and pasted the file system from the sda2 Windows XP partition into the new extended partition making a new partition, which became /dev/sda5.
(c) I deleted the Windows XP partition /dev/sda2.
(d) I set the boot flag on /dev/sda5, Windows XP in the logical partition.

2. With the Windows boot loader still installed to MBR since the end of [post #19]("http://ubuntuforums.org/showpost.php?p=10255411&postcount=19"),  I tried to boot Windows XP but I wasn't able to, instead I was shown the error message 'DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER' which I think is an error message from the BIOS.

3. I booted Parted Magic Live CD again and I tried setting the boot flag in the extended partition instead.
4. On reboot I was given a blinking cursor in the lower left corner of the monitor.

5. I used the Ubuntu Maverick Meerkat Live CD to re-install GRUB from one of my Maverick Meerkat installations in the other hard disk in the same computer.

6. I set the boot flag in the logical partition /dev/sda5 (Windows XP) again.

7. On reboot, I selected Windows XP from the grub menu and it booted.

**Conclusion:**
Windows XP's own boot loader cannot boot Windows XP in a logical partition but GNU/GRUB can do it. The trick here is to use GParted to set the boot flag on it first, the last time I tried GRUB was able to set the boot flag with its 'makeactive' command but it only worked for primary partitions.

So Windows XP can be booted in a logical partition, at least in the computer I have.
I would be interested to hear if this works for others or not.  :)

Here is the RESULTS.txt, 
 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /grub/menu.lst /boot.ini /grldr /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Fat16
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1          81,922,048   156,301,311    74,379,264   5 Extended
/dev/sda5    *     81,924,096   156,301,311    74,377,216   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    74,272,768    74,270,721  83 Linux
/dev/sdb2         130,756,606   156,301,311    25,544,706   5 Extended
/dev/sdb5         150,290,432   156,301,311     6,010,880  82 Linux swap / Solaris
/dev/sdb6         130,756,608   150,288,383    19,531,776  83 Linux
/dev/sdb3          74,274,816   130,754,559    56,479,744  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda5        2629-16F0                              vfat       WINDOWS XP                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        ec345b87-039c-4bb8-901d-d08acc968cd6   ext4                                     
/dev/sdb5        af407266-0dff-4698-9fc5-9f3b764bd0f3   swap                                     
/dev/sdb6        6655ee5e-45d1-4d1c-9a7d-10f30f16e745   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext4       (rw,errors=remount-ro,commit=0)


============================= sda5/grub/menu.lst: =============================

timeout 10 
 
title Windows at (hd0,0) 
root (hd0,0) 
chainloader +1
================================ sda5/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /FASTDETECT /NOEXECUTE=OPTIN 
c:\GRLDR="Start Grub"  

=================== sda5: Location of files loaded by Grub: ===================


    ??GB: grub/menu.lst

=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
insmod play
play 480 900 2 1000 2 800 2 400 2 600 3
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=red/yellow
set menu_color_highlight=light-magenta/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2629-16f0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=af407266-0dff-4698-9fc5-9f3b764bd0f3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  69.3GB: boot/grub/core.img
  73.8GB: boot/grub/grub.cfg
  70.4GB: boot/initrd.img-2.6.32-21-generic
  75.1GB: boot/initrd.img-2.6.32-24-generic
  70.3GB: boot/vmlinuz-2.6.32-21-generic
  74.7GB: boot/vmlinuz-2.6.32-24-generic
  75.1GB: initrd.img
  70.4GB: initrd.img.old
  74.7GB: vmlinuz
  70.3GB: vmlinuz.old

=========================== sdb3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda5)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2629-16f0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=af407266-0dff-4698-9fc5-9f3b764bd0f3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


  57.4GB: boot/grub/core.img
  55.6GB: boot/grub/grub.cfg
  38.5GB: boot/initrd.img-2.6.35-22-generic
  40.8GB: boot/initrd.img-2.6.35-23-generic
  57.4GB: boot/vmlinuz-2.6.35-22-generic
  57.5GB: boot/vmlinuz-2.6.35-23-generic
  40.8GB: initrd.img
  38.5GB: initrd.img.old
  57.5GB: vmlinuz
  57.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  e9 90 b3 f8 ff b8 0c c0  14 60 e9 35 83 fc ff cc  |.........`.5....|
00000010  cc cc cc cc 8d 4d 8c e9  6f b8 f8 ff 8d 8d 7c fe  |.....M..o.....|.|
00000020  ff ff e9 c0 e6 f9 ff 8d  8d 78 fd ff ff e9 b5 e6  |.........x......|
00000030  f9 ff b8 40 c0 14 60 e9  08 83 fc ff cc cc cc cc  |...@..`.........|
00000040  cc 8d 4d ec e9 68 d1 f8  ff 8d 4d e8 e9 60 d1 f8  |..M..h....M..`..|
00000050  ff 8d 4d f0 e9 58 d1 f8  ff ff 75 08 e8 f9 44 f9  |..M..X....u...D.|
00000060  ff 59 c3 b8 7c c0 14 60  e9 d7 82 fc ff cc cc cc  |.Y..|..`........|
00000070  cc cc 8d 4d f0 e9 37 d1  f8 ff b8 a0 c0 14 60 e9  |...M..7.......`.|
00000080  c0 82 fc ff cc cc cc cc  cc 8d 4d c8 e9 1f e6 f9  |..........M.....|
00000090  ff b8 c4 c0 14 60 e9 a9  82 fc ff cc cc cc cc cc  |.....`..........|
000000a0  8d 4d dc e9 31 cd f8 ff  b8 e8 c0 14 60 e9 92 82  |.M..1.......`...|
000000b0  fc ff cc cc cc cc cc 8d  4d d8 e9 cc b7 f8 ff 8d  |........M.......|
000000c0  4d e4 e9 ea d0 f8 ff 8d  4d ec e9 e2 d0 f8 ff 8d  |M.......M.......|
000000d0  4d e8 e9 da d0 f8 ff b8  24 c1 14 60 e9 63 82 fc  |M.......$..`.c..|
000000e0  ff cc cc cc cc cc 8d 4d  e8 e9 c6 b7 f8 ff 8d 4d  |.......M.......M|
000000f0  dc e9 95 b7 f8 ff b8 84  c1 14 60 e9 44 82 fc ff  |..........`.D...|
00000100  cc cc cc cc cc 8d 4d e8  e9 a7 b7 f8 ff 8d 4d dc  |......M.......M.|
00000110  e9 76 b7 f8 ff b8 e4 c1  14 60 e9 25 82 fc ff cc  |.v.......`.%....|
00000120  cc cc cc cc 8d 4d e8 e9  88 b7 f8 ff 8d 4d dc e9  |.....M.......M..|
00000130  57 b7 f8 ff b8 44 c2 14  60 e9 06 82 fc ff cc cc  |W....D..`.......|
00000140  cc cc cc 8d 4d ec e9 40  b7 f8 ff b8 68 c2 14 60  |....M..@....h..`|
00000150  e9 ef 81 fc ff cc cc cc  cc cc 8d 4d 8c e9 29 b7  |...........M..).|
00000160  f8 ff 8d 4d a0 e9 47 d0  f8 ff ff 75 a4 e8 e8 43  |...M..G....u...C|
00000170  f9 ff 59 c3 8d 4d 98 e9  49 cc f8 ff b8 a4 c2 14  |..Y..M..I.......|
00000180  60 e9 be 81 fc ff cc cc  cc cc cc 8d 4d ec e9 21  |`...........M..!|
00000190  b7 f8 ff 8d 4d dc e9 f0  b6 f8 ff b8 04 c3 14 60  |....M..........`|
000001a0  e9 9f 81 fc ff cc cc cc  cc cc 8d 4d cc e9 13 cc  |...........M....|
000001b0  f8 ff 8d 4d d8 e9 f7 cf  f8 ff 8b 4d e0 e9 80 fe  |...M.......M....|
000001c0  ff ff 0b fe ff ff 00 08  00 00 00 e8 6e 04 00 00  |............n...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  ec 5c 8b 5d 08 85 db 27  b2 65 c5 63 50 25 5f 16  |.\.]...'.e.cP%_.|
00000010  d3 8b 8a 22 68 32 a3 11  8b 52 7c ac 11 03 c1 73  |..."h2...R|....s|
00000020  39 8b bb 98 4c ba 00 04  8d 0c 8a 89 4d b4 85 ff  |9...L.......M...|
00000030  74 0f 8d 47 08 39 47 08  89 45 b0 0f 85 05 71 d2  |t..G.9G..E....q.|
00000040  55 12 b5 19 0b 22 04 ac  4a 1e f7 60 42 dd 65 f4  |U...."..J..`B.e.|
00000050  98 22 50 22 25 d6 b7 8b  b8 68 08 01 85 ff 74 d2  |."P"%....h....t.|
00000060  26 87 b3 b8 74 c7 29 f8  b2 22 16 fc e8 80 22 74  |&...t.).."...."t|
00000070  27 03 4d b8 8d 45 c4 89  22 66 5f 04 24 13 94 09  |'.M..E.."f_.$...|
00000080  03 4c 24 04 e8 82 f9 23  cf 25 8b 75 c4 6a 1c 48  |.L$....#.%.u.j.H|
00000090  06 40 16 07 45 b8 8b 18  39 f3 75 08 eb 2c 23 fb  |.@..E...9.u..,#.|
000000a0  b2 26 8b 53 74 10 05 f3  8b 4a 04 85 c9 74 ec 23  |.&.St....J...t.#|
000000b0  f9 b2 e6 fc b3 01 14 24  ff d1 77 04 75 da 8b 78  |.......$..w.u..x|
000000c0  0b 01 bc 89 75 dc 22 88  af 22 dc b2 77 0b a4 f9  |....u.".."..w...|
000000d0  ec 2e df b2 0f 84 e6 49  1e 0f 2b 8e b1 0f 85 22  |.......I..+...."|
000000e0  10 3c 04 80 7f 04 00 0f  84 08 44 5f 22 5d 3d 5d  |.<........D_"]=]|
000000f0  22 78 3b 01 fb fe ff ff  29 2c 03 23 35 8a b4 22  |"x;.....),.#5.."|
00000100  c0 3d 01 55 b0 8d 45 12  95 03 0c 64 0d 22 a0 62  |.=.U..E....d.".b|
00000110  12 56 04 b6 f8 cc 19 23  ee 8f 7c 05 4c 19 01 4d  |.V.....#..|.L..M|
00000120  b0 8b 19 8d 19 2e 76 14  74 28 94 64 08 66 90 74  |......v.t(.d.f.t|
00000130  f1 8b 50 04 85 d2 74 ea  97 19 e4 8b 4d 22 29 8a  |..P...t.....M").|
00000140  89 12 e5 37 d2 7f 04 75  d8 8b 61 0c c8 29 34 03  |...7...u..a..)4.|
00000150  7e 0b d6 f8 30 36 03 85  32 9d cb b0 74 27 01 f6  |~...06..2...t'..|
00000160  f7 ec ff 69 17 62 22 41  28 40 5b c6 8b 45 b8 22  |...i.b"A(@[..E."|
00000170  00 51 07 de f7 ec ff eb  e6 89 45 ac 0f 2a 9e b5  |.Q........E..*..|
00000180  3b 0f 2b 0d 04 75 29 9d  b5 61 22 f4 30 03 4d 08  |;.+..u)..a".0.M.|
00000190  85 c9 74 0b 22 68 20 02  14 24 e8 fb 5e 71 19 ac  |..t."h ..$..^q..|
000001a0  22 5d eb 44 7e 1f 5d b8  61 0e 85 c2 0e f1 0f 40  |"].D~.].a......@|
000001b0  0c 07 ce 8b 55 b8 89 45  ac 8d 45 c0 f8 16 00 fe  |....U..E..E.....|
000001c0  ff ff 82 fe ff ff 02 10  2a 01 00 b8 5b 00 00 fe  |........*...[...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 08 2a 01 00 00  |............*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 


```

---

### Post by oldfred on 2010-12-19
Herman,
I have a link to one of meierfra. posts (were you part of that one on another?) where he made XP work in a logical partition. He also mentioned that the Lilo boot loader will then boot windows in the logical. I think the windows MBR boot loader only boots if it is a primary partition. 

Edit to add links - as long as we are adding boot issue solutions:
How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

We have also seen some BIOS (some Intel boards, maybe others) that will not even let you start booting unless you have a boot flag on a primary parititon and even if it is gpt. Note that gpt is not supposed to have boot flags.

I have also seen where the bootscript shows that the partition location is inconsistent. Something like start is one sector in boot partition but is really another sector. I assume this is because the partition was copied. I see users copying there windows to another logical partition and expecting it to work. It sounds like your test is saying the newest version of Parted Magic is also fixing up the partition boot sector?

Maybe why testdisk is better to repair NTFS boot sector per meierfra. as then it would work on a drive that is not first. I also sometimes have had users have boot issues that we were not really able to solve with windows as the second drive.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Herman on 2010-12-19
:D Thanks for those links, oldfred. Yes, we learned a lot from meierfra. 
I am still thinking about why I did not need to edit boot.ini every time I changed its partition number. I am trying to remember something meierfa said about the way Windows XP  counts partition numbers for the purposes of the boot.ini file. 
> Maybe why testdisk is better to repair NTFS boot sector per meierfra. as  then it would work on a drive that is not first. I also sometimes have  had users have boot issues that we were not really able to solve with  windows as the second drive.Yes, that makes sense, I think you're right.
> It sounds like your test is saying the newest version of Parted Magic is also fixing up the partition boot sector?Well I could try an experiment to examine that and compare the latest version, which is at the time of typing this, GParted 0.7.0, in Parted Magic Live CD version 5.7.

One of the big problems GParted has been plagued with over time is the number of old versions of the software people keep lying around in their drawers and under piles of other old CDs. 
Naturally, we cannot expect old software to have been designed by gypsies with crystal balls that can see into the future and anticipate changes like the introduction of the ext4 file system for GNU/Linux distros and the BCD loader and the changes associated with that like the 2048 sector alignment which were seen for the first time when Vista first came out and departed quite unexpectedly from long established conventions.
Therefore, it's always important to remind people and stress that they should always be using a recent version of GParted. 

Ubuntu Maverick Meerkat features GParted version 0.6.2 now in the 'Desktop' Live/Install CD, and people should use at least that version or newer, and throw away or mothball the older GParted versions, since those are past their 'use-by date'. :)

---

### Post by Herman on 2010-12-19
:D Okay, thanks to oldfred's links, I have found what meierfra said about the way Windows XP numbers partitions for the purposes of the boot.ini file,
 > The number in ``partition(1)'' needs to be changed to the correct  number for your XP partition. 
Windows starts counting at 1 and counts  partitions in the order of the partition table (so far that's the same  way linux counts) BUT skips over extended partitions and empty  partitions.This explains why I was able to copy Windows XP from partition number1 to other partition numbers without the need to update the boot.ini file with the correct partition number each time and so far I have been able to get away with it in earlier experiments without a hitch. 
Windows does not count partition numbers the same way we expect it to, 'Windows starts counting at 1 and counts  partitions in the order of the partition table (so far that's the same  way linux counts) ***BUT skips over extended partitions and empty  partitions***."
So because it was in the only partition on the drive, it was still counting itself as number 1, even though the real partition number it was in was 2 or 5.

In this experiment I will deliberately 'bork' Windows XP in the logical partition where I last left it back in [post #22]("http://ubuntuforums.org/showpost.php?p=10255691&postcount=22") merely by installing Ubuntu.

**Aim:**
This experiment is to see what happens when Windows idea of how to count partition numbers can come unstuck when a new partition is added, and how to fix it.
In this particular example, I will demonstrate what happens when the new partition is created for the purposes of installing Ubuntu in, because that's the scenario boot loader experts usually see here in Ubuntu Web Forums.
The same effect can probably be obtained just by creating a new empty partition though, nevermind whether Ubuntu, GParted or GRUB have anything to do with it.
Windows does not need to be in a logical partition for this to happen, probably any partition number other than 1 will allow this situation to eventuate.

**Method:**
I left Windows in a non-first partition, (in partition #5 where it was booting in a logical partition in the last experiment), and created an new partition and installed Ubuntu in it.

**Result:**
Ubuntu boots fine.
When I try to boot Windows XP via Ubuntu's GRUB I get,
```
Windows could not start because the following file is missing
or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file.
```**Probable Cause:**
Because of the rather odd way Windows counts its partitions for partition numbering purposes in boot.ini, Windows still counted itself as 'partition number 1 ' in boot.ini when it was really in partition number 5 according to the way we count partitions in Linux.

**Solution:**
Edit boot.ini and change the partition number to '2', since now Windows is in number 2 position according to it's peculiar numbering rules.

**Result:**
Windows XP boots again. :D
```
gksudo gedit /media/WINDOWS\ XP/boot.ini
``````
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(**[COLOR=Red]1[/COLOR]**)\WINDOWS="Microsoft Windows XP Home Edition" /FASTDETECT /NOEXECUTE=OPTIN
c:\GRLDR="Start Grub" 
``````
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition([COLOR=Blue]**2**[/COLOR])\WINDOWS="Microsoft Windows XP Home Edition" /FASTDETECT /NOEXECUTE=OPTIN
c:\GRLDR="Start Grub" 
```RESULTS.txt
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /grub/menu.lst /boot.ini /grldr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Fat16
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1          81,924,094   156,301,311    74,377,218   5 Extended
/dev/sda5    *     81,924,096   156,301,311    74,377,216   b W95 FAT32
/dev/sda2               2,048    81,922,047    81,920,000  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    74,272,768    74,270,721  83 Linux
/dev/sdb2         130,756,606   156,301,311    25,544,706   5 Extended
/dev/sdb5         150,290,432   156,301,311     6,010,880  82 Linux swap / Solaris
/dev/sdb6         130,756,608   150,288,383    19,531,776  83 Linux
/dev/sdb3          74,274,816   130,754,559    56,479,744  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        8fe48325-006f-4ef5-9046-e678364721f0   ext4                                     
/dev/sda5        2629-16F0                              vfat       WINDOWS XP                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        ec345b87-039c-4bb8-901d-d08acc968cd6   ext4                                     
/dev/sdb5        af407266-0dff-4698-9fc5-9f3b764bd0f3   swap                                     
/dev/sdb6        6655ee5e-45d1-4d1c-9a7d-10f30f16e745   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/8fe48325-006f-4ef5-9046-e678364721f0 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb3        /media/ec345b87-039c-4bb8-901d-d08acc968cd6 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/WINDOWS XP        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


============================= sda5/grub/menu.lst: =============================

timeout 10 
 
title Windows at (hd0,0) 
root (hd0,0) 
chainloader +1
================================ sda5/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /FASTDETECT /NOEXECUTE=OPTIN 
c:\GRLDR="Start Grub"  

=================== sda5: Location of files loaded by Grub: ===================


    ??GB: grub/menu.lst

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 8fe48325-006f-4ef5-9046-e678364721f0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 8fe48325-006f-4ef5-9046-e678364721f0
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8fe48325-006f-4ef5-9046-e678364721f0
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8fe48325-006f-4ef5-9046-e678364721f0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8fe48325-006f-4ef5-9046-e678364721f0
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8fe48325-006f-4ef5-9046-e678364721f0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8fe48325-006f-4ef5-9046-e678364721f0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8fe48325-006f-4ef5-9046-e678364721f0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda5)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2629-16f0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdb3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdb3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=8fe48325-006f-4ef5-9046-e678364721f0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=af407266-0dff-4698-9fc5-9f3b764bd0f3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  13.1GB: boot/grub/grub.cfg
   9.0GB: boot/initrd.img-2.6.35-22-generic
  21.6GB: boot/vmlinuz-2.6.35-22-generic
   9.0GB: initrd.img
  21.6GB: vmlinuz

=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
insmod play
play 480 900 2 1000 2 800 2 400 2 600 3
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=red/yellow
set menu_color_highlight=light-magenta/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2629-16f0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e511de5f-1abb-4011-bf56-128f16f7663b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e511de5f-1abb-4011-bf56-128f16f7663b ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=af407266-0dff-4698-9fc5-9f3b764bd0f3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  69.3GB: boot/grub/core.img
  73.8GB: boot/grub/grub.cfg
  70.4GB: boot/initrd.img-2.6.32-21-generic
  75.1GB: boot/initrd.img-2.6.32-24-generic
  70.3GB: boot/vmlinuz-2.6.32-21-generic
  74.7GB: boot/vmlinuz-2.6.32-24-generic
  75.1GB: initrd.img
  70.4GB: initrd.img.old
  74.7GB: vmlinuz
  70.3GB: vmlinuz.old

=========================== sdb3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set ec345b87-039c-4bb8-901d-d08acc968cd6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda5)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2629-16f0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 6655ee5e-45d1-4d1c-9a7d-10f30f16e745
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=6655ee5e-45d1-4d1c-9a7d-10f30f16e745 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=ec345b87-039c-4bb8-901d-d08acc968cd6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=af407266-0dff-4698-9fc5-9f3b764bd0f3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


  57.4GB: boot/grub/core.img
  55.6GB: boot/grub/grub.cfg
  38.5GB: boot/initrd.img-2.6.35-22-generic
  40.8GB: boot/initrd.img-2.6.35-23-generic
  57.4GB: boot/vmlinuz-2.6.35-22-generic
  57.5GB: boot/vmlinuz-2.6.35-23-generic
  40.8GB: initrd.img
  38.5GB: initrd.img.old
  57.5GB: vmlinuz
  57.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  63 00 61 00 6c 00 65 00  6e 00 64 00 61 00 72 00  |c.a.l.e.n.d.a.r.|
00000010  20 00 6f 00 72 00 20 00  74 00 68 00 65 00 20 00  | .o.r. .t.h.e. .|
00000020  63 00 6f 00 6e 00 74 00  61 00 69 00 6e 00 69 00  |c.o.n.t.a.i.n.i.|
00000030  6e 00 67 00 20 00 6d 00  61 00 69 00 6c 00 62 00  |n.g. .m.a.i.l.b.|
00000040  6f 00 78 00 2e 00 0d 00  0a 00 25 00 6e 00 25 00  |o.x.......%.n.%.|
00000050  6e 00 46 00 6f 00 72 00  20 00 6d 00 6f 00 72 00  |n.F.o.r. .m.o.r.|
00000060  65 00 20 00 69 00 6e 00  66 00 6f 00 72 00 6d 00  |e. .i.n.f.o.r.m.|
00000070  61 00 74 00 69 00 6f 00  6e 00 2c 00 20 00 63 00  |a.t.i.o.n.,. .c.|
00000080  6c 00 69 00 63 00 6b 00  20 00 68 00 74 00 74 00  |l.i.c.k. .h.t.t.|
00000090  70 00 3a 00 2f 00 2f 00  77 00 77 00 77 00 2e 00  |p.:././.w.w.w...|
000000a0  6d 00 69 00 63 00 72 00  6f 00 73 00 6f 00 66 00  |m.i.c.r.o.s.o.f.|
000000b0  74 00 2e 00 63 00 6f 00  6d 00 2f 00 63 00 6f 00  |t...c.o.m./.c.o.|
000000c0  6e 00 74 00 65 00 6e 00  74 00 72 00 65 00 64 00  |n.t.e.n.t.r.e.d.|
000000d0  69 00 72 00 65 00 63 00  74 00 2e 00 61 00 73 00  |i.r.e.c.t...a.s.|
000000e0  70 00 2e 00 0d 00 0a 00  00 00 00 00 38 01 01 00  |p...........8...|
000000f0  43 00 61 00 6c 00 65 00  6e 00 64 00 61 00 72 00  |C.a.l.e.n.d.a.r.|
00000100  20 00 61 00 67 00 65 00  6e 00 74 00 20 00 66 00  | .a.g.e.n.t. .f.|
00000110  61 00 69 00 6c 00 65 00  64 00 20 00 74 00 6f 00  |a.i.l.e.d. .t.o.|
00000120  20 00 64 00 65 00 74 00  65 00 72 00 6d 00 69 00  | .d.e.t.e.r.m.i.|
00000130  6e 00 65 00 20 00 74 00  68 00 65 00 20 00 70 00  |n.e. .t.h.e. .p.|
00000140  72 00 69 00 6d 00 61 00  72 00 79 00 20 00 63 00  |r.i.m.a.r.y. .c.|
00000150  61 00 6c 00 65 00 6e 00  64 00 61 00 72 00 20 00  |a.l.e.n.d.a.r. .|
00000160  66 00 6f 00 72 00 20 00  6d 00 61 00 69 00 6c 00  |f.o.r. .m.a.i.l.|
00000170  62 00 6f 00 78 00 3a 00  20 00 25 00 31 00 2e 00  |b.o.x.:. .%.1...|
00000180  0d 00 0a 00 25 00 6e 00  25 00 6e 00 46 00 6f 00  |....%.n.%.n.F.o.|
00000190  72 00 20 00 6d 00 6f 00  72 00 65 00 20 00 69 00  |r. .m.o.r.e. .i.|
000001a0  6e 00 66 00 6f 00 72 00  6d 00 61 00 74 00 69 00  |n.f.o.r.m.a.t.i.|
000001b0  6f 00 6e 00 2c 00 20 00  63 00 6c 00 69 00 80 fe  |o.n.,. .c.l.i...|
000001c0  ff ff 0b fe ff ff 02 00  00 00 00 e8 6e 04 00 00  |............n...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  ec 5c 8b 5d 08 85 db 27  b2 65 c5 63 50 25 5f 16  |.\.]...'.e.cP%_.|
00000010  d3 8b 8a 22 68 32 a3 11  8b 52 7c ac 11 03 c1 73  |..."h2...R|....s|
00000020  39 8b bb 98 4c ba 00 04  8d 0c 8a 89 4d b4 85 ff  |9...L.......M...|
00000030  74 0f 8d 47 08 39 47 08  89 45 b0 0f 85 05 71 d2  |t..G.9G..E....q.|
00000040  55 12 b5 19 0b 22 04 ac  4a 1e f7 60 42 dd 65 f4  |U...."..J..`B.e.|
00000050  98 22 50 22 25 d6 b7 8b  b8 68 08 01 85 ff 74 d2  |."P"%....h....t.|
00000060  26 87 b3 b8 74 c7 29 f8  b2 22 16 fc e8 80 22 74  |&...t.).."...."t|
00000070  27 03 4d b8 8d 45 c4 89  22 66 5f 04 24 13 94 09  |'.M..E.."f_.$...|
00000080  03 4c 24 04 e8 82 f9 23  cf 25 8b 75 c4 6a 1c 48  |.L$....#.%.u.j.H|
00000090  06 40 16 07 45 b8 8b 18  39 f3 75 08 eb 2c 23 fb  |.@..E...9.u..,#.|
000000a0  b2 26 8b 53 74 10 05 f3  8b 4a 04 85 c9 74 ec 23  |.&.St....J...t.#|
000000b0  f9 b2 e6 fc b3 01 14 24  ff d1 77 04 75 da 8b 78  |.......$..w.u..x|
000000c0  0b 01 bc 89 75 dc 22 88  af 22 dc b2 77 0b a4 f9  |....u.".."..w...|
000000d0  ec 2e df b2 0f 84 e6 49  1e 0f 2b 8e b1 0f 85 22  |.......I..+...."|
000000e0  10 3c 04 80 7f 04 00 0f  84 08 44 5f 22 5d 3d 5d  |.<........D_"]=]|
000000f0  22 78 3b 01 fb fe ff ff  29 2c 03 23 35 8a b4 22  |"x;.....),.#5.."|
00000100  c0 3d 01 55 b0 8d 45 12  95 03 0c 64 0d 22 a0 62  |.=.U..E....d.".b|
00000110  12 56 04 b6 f8 cc 19 23  ee 8f 7c 05 4c 19 01 4d  |.V.....#..|.L..M|
00000120  b0 8b 19 8d 19 2e 76 14  74 28 94 64 08 66 90 74  |......v.t(.d.f.t|
00000130  f1 8b 50 04 85 d2 74 ea  97 19 e4 8b 4d 22 29 8a  |..P...t.....M").|
00000140  89 12 e5 37 d2 7f 04 75  d8 8b 61 0c c8 29 34 03  |...7...u..a..)4.|
00000150  7e 0b d6 f8 30 36 03 85  32 9d cb b0 74 27 01 f6  |~...06..2...t'..|
00000160  f7 ec ff 69 17 62 22 41  28 40 5b c6 8b 45 b8 22  |...i.b"A(@[..E."|
00000170  00 51 07 de f7 ec ff eb  e6 89 45 ac 0f 2a 9e b5  |.Q........E..*..|
00000180  3b 0f 2b 0d 04 75 29 9d  b5 61 22 f4 30 03 4d 08  |;.+..u)..a".0.M.|
00000190  85 c9 74 0b 22 68 20 02  14 24 e8 fb 5e 71 19 ac  |..t."h ..$..^q..|
000001a0  22 5d eb 44 7e 1f 5d b8  61 0e 85 c2 0e f1 0f 40  |"].D~.].a......@|
000001b0  0c 07 ce 8b 55 b8 89 45  ac 8d 45 c0 f8 16 00 fe  |....U..E..E.....|
000001c0  ff ff 82 fe ff ff 02 10  2a 01 00 b8 5b 00 00 fe  |........*...[...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 08 2a 01 00 00  |............*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
```

---

