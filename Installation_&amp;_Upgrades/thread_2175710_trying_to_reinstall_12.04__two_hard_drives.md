---
title: "trying to reinstall 12.04 / two hard drives"
date: 2013-09-20
forum: Installation &amp; Upgrades
---

### Post by jgw on 2013-09-20
I am trying to reinstall 12.04  I am also confused in the installation site.  I see /dev/sda, /dev/sdb  /dev/sda1, /dev/sdb1  I am told "select Ubuntu system partition, set its mount point as "/"".  This is where I lose my way.  I have two hard drives on this machine and have chosen the one where the existing system is installed (format is ext4) and its got lots of space on it.  The drive I want to deal with is sdb1/ext4.  I can edit that partition (ext4 journaling file system and change the mount point to "/").  As far as I can tell this is what I am supposed to do.  I would also like to save part or all of my existing home directory.  I can't seem to be able to move a large folder from that drive to the other drive (no permissions, and no way to set same)  and I am in the midst of running the install.  I have unchecked the format option but am not sure that the reinstall will not overwrite my existing home directory.  Any help on this one is appreciated

Thank you...............

---

### Post by Bashing-om on 2013-09-20
jgw; Hi !

Kinda confusing as to what you have and to what you want to do.
Hard drives .. :
1st HD is 'sda"
2nd HD is "sdb"
Now the Hard Drives get cut up into useable sections termed "partitions"
Partition scheme:
sda1 is the 1st partiton on the 1st hard drive
sda2 is the 2nd partition on that 1st hard drive
sda5 is the 5th partition on that 1st hard drive
sdb1 is the 1st partition on the 2nd hard drive
sdb6 would be the 6th partition on that hypothetical 2nd Hard Drive.

OK .. here is what I envision is your case; You presently have ubuntu installed onto that first hard drive in a unknown number of partitions .. maybe two partitons (minimum -> "/" and swap). maybe more ..depends on how you installed. Now, you want to INSTALL ubuntu onto the second hard drive (sdb) ... and you have set up the partitions in GParted before hand to allow for installation onto separate partitions for at least "/", "/home" and swap ?? This takes a bit of know how or a lot of wanting to know, to do ... Once you have done it .. nothing to it ! Installing to separate partitions takes planning and preparation ... most important is the size to allocate to each partition .. that size factor is a determination made of the use characterization of your system.

For now show us how you Hard Disk are set up; Post back the output - between code (#) tags - of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```

IF your present home is on sda and the new install is to be on sdb .. one may - at a later time - copy old home to new home, which may be the easier thing to do.
Give consideration to booting, that determines where you will install grub and what other operating systems you are booting and how you want to boot your system. Only you can know. all we can do is advise.

And yeah, you are still confused ! .. We will work with you to change that state of mind !
Starting with the outputs .. and a clarification of what you want to do.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by jgw on 2013-09-20
Thank you for the reply.

Here are the results of your commands.  My linux drive sdb (hitachi, file system ext4)   Forgot, I am reinstalling because I have seriously screwed up and the system is no longer booting.  I guess I should also mention that I tried to use a 12.04.3 to do this install but when I ran that the video output stopped.  This will be a pure usbuntu machine, no other operating system on it.  
anyway, here are the results:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6eb74cc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1953520064   976760001   42  SFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00010c4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1945139199   972568576   83  Linux
/dev/sdb2      1945141246  1953523711     4191233    5  Extended
/dev/sdb5      1945141248  1953523711     4191232   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10EALX-009 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ntfs


Model: ATA Hitachi HDT72101 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  996GB   996GB   primary   ext4            boot
 2      996GB   1000GB  4292MB  extended
 5      996GB   1000GB  4292MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA WDC WD10EALX-009 (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End          Size         Type     File system  Flags
 1      63s    1953520064s  1953520002s  primary  ntfs

ubuntu@ubuntu:~$ sudo parted /dev/sdb unit s print
Model: ATA Hitachi HDT72101 (scsi)
Disk /dev/sdb: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start        End          Size         Type      File system     Flags
 1      2048s        1945139199s  1945137152s  primary   ext4            boot
 2      1945141246s  1953523711s  8382466s     extended
 5      1945141248s  1953523711s  8382464s     logical   linux-swap(v1)

ubuntu@ubuntu:~$ lsblk -f
NAME   FSTYPE  LABEL                   MOUNTPOINT
sda                                    
&#9492;&#9472;sda1                                 
sdb                                    
&#9500;&#9472;sdb1                                 
&#9500;&#9472;sdb2                                 
&#9492;&#9472;sdb5                                 [SWAP]
sr0    iso9660 Ubuntu 12.04.2 LTS i386 /cdrom
loop0                                  /rofs
ubuntu@ubuntu:~$

---

### Post by Bashing-om on 2013-09-20
jgw; Well..
You have Windows installed to the 1st hard drive sda;
You have "linux" installed and bootable in the 2nd Hard Drive, taking up almost all the disk space .. maybe what you want maybe not,,,
In and of it's self not bad ,, just not good usage of that huge hard drive !...
If all you want is to get up and running, then in the installer - something else option - install to sdb, 
make sure "/" is defined and checked to format .. and "/home' is NOT checked to format, 
reuse the present swap partition.
Always always have backup of any data important to you ... Murphy's law always applies !
Install grub onto "sdb" ... and set in bios to boot "sdb" as 1st boot priority -> will chainload Windows for booting choice and not touch Windows' boot code.
Why you have swap in an extended partition that takes up all that extended partition, I can not fathom .. but that arrangement will work.

But to be as honest as possible .. I would (re-)partition sdb.
I do prefer separate partitions for "/" and "/Home" and a partition set up for sharing data between operating systems - in your case an NTFS partition.
One gains much finer control of the system at large as well as expanded options for disk usage and access.
For instance, my system:
> 
[sudo] password for sysop: 
/dev/sda1: LABEL="1304mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1304mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1204" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1304mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="ubie1204" UUID="5bae8c40-b15d-42f8-9fc9-0cf087f338d4" TYPE="ext4" 
sysop@1304mini:~$


This is a WORK, STORAGE, backup OS, and a testing OS installation. For the way I use my system.

In your case .. (re)partitioning "sdb" is a great opportunity for learning ! This is ubuntu, whatever miss happens, with backups and a liveDVD it is fixable !

[INDENT][INDENT]whatcha gonna do
[/INDENT][/INDENT]

---

### Post by jgw on 2013-09-20
Thanks for the reply.....

The reason that windows is installed on that drive is because it used to be a windows system.   When I installed ubuntu, onto the other drive, I just let the installer do its thing and that is how it partitioned the drive.  I would love to reformat the entire drive but I have not been able to figure out how to get stuff off that drive (sdb)  If I try and do it with the sample ubuntu, on the cd (test) I do not have permissions to do anything on the two drives.  If I try and take out the ubuntu drive and deal with it in windows then windows doesn't recognize the file system.  Kinda between a rock and a hard place.  

The directions for installing whilst saving home say to format NOTHING and just let it do its thing.  I have no idea what might happen.  If it creates a new new home directory, and does not format, in theory the old home should be there too?  There is, incidentally, something over 400gb left on the ubuntu drive.  What I am tempted to do is to set the "/" for sdb and just let it have at it with no formatting.  Whaddya think?

---

### Post by Bashing-om on 2013-09-20
jgw; Wheeelll,

Re-install is your goal .. so in order to (re)install the operating system .."/" must be formatted,
as /home is not marked to format ..then in theory your files and configs will not be overwritten.

Access from the liveDVD to the hard drive: -> Here is but one way;
 Boot the liveDVD to terminal:
```

sudo mkdir /mnt/test
sudo mount /dev/sdb1 /mnt/test
ls -la /mnt/test/home/<your_user_name>

```
Look around .. you see the your /home directory on sdb ..
you may Change Directory as desired to make thing easier and; 
Copy whatever you want off to an external device.
When done ...most most important that you (UN)Mount "sdb" else file system corruption at some level will indeed result !
You mounted it manually you MUST UNMount it manually.
```

sudo umount /mnt/test

```

try this and see ... any additional questions , ask .. ya need to be comfortable with what you are doing !
There are no stupid questions !


[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2013-09-20
At the moment you have partitions arranged in what is the default installation of ubuntu, ie, a root partition as primary partition sda1, an extended partition sda2 and filling that a logical partition as swap, sda5.  That is quite normal, and Bashing-om's remark query about why you have a swap taking all the extended sda2 shows he is more advanced, and has always used manual partitioning, the "Something Else" when you get to that point in installation.

Bashing-om also says> If all you want is to get up and running, then in the installer - something else option - install to sdb, 
make sure "/" is defined and checked to format .. and "/home' is NOT checked to format, 
reuse the present swap partition. but if you do that without first backing up your home contents, including all the hidden folders and files you will lose all your own files as you do not have a separate /home at the moment.

So I recommend the following:-
[LIST=1]
[*]Backup all your home folders and files to an external disk if you have one, either flash drive or external hard drive, or even to DVDs if necessary.
[*]Boot to your install medium and when you get to the partitioning stage use "Something Else".
[*]This will show you all the partitions on the machine's disks.  If I were you I would now delete all the partitions to avoid your new partition numbers being out of order.
[*]Now choose to make a new partition sdb1 of 20GB.  Make it ext4, the mountpoint as /, and select to format the partition.
[*]This will leave a lot of unallocated space so make a new extended partition in all that space.  This will be a new sdb2.
[*]Now make another new logical partition in the extended partition using all except the final 4GB and set the mountpoint of this new sdb5 as /home, and just for this first time select to format the partition.  *If you need to reinstall in the future you will select the same /home mountpoint for this partition but will not format it, so all your own files and folders will be untouched.*
[*]In the final unallocated 4Gb make a new swap partition.  This will now be sdb6.
[*]Carry on installing and once you have done so restore the backed up /home folders and files to the new home.
[/LIST]
This may sound very complicated at the moment, but I think that once you start you will see the logical progression of what is happening and the whole procedure will appear easier than it sounds and serve you very well for the future when installing or upgrading your OS.

---

### Post by jgw on 2013-09-20
My problem remains.  I attached an external drive to the system, its recognized and mounted.  I also have my home directory up.  However, when I try to copy from one (home) to the other (external drive) it tells me I cannot do it because I do not have permission.  I got to this place by putting in the live dvd and booted it up in test mode.  I did not goto the install screen(s)  I also entered the commands you suggested (which is how I got to my old home folder).   Got any ideas as to how to get permissions (log in) ?  Oh, when I entered your commands, with the sudo, it did not once ask me to login.  This is strange?

---

### Post by ajgreeny on 2013-09-20
> **jgw said:**
> My problem remains.  I attached an external drive to the system, its recognized and mounted.  I also have my home directory up.  However, when I try to copy from one (home) to the other (external drive) it tells me I cannot do it because I do not have permission.  I got to this place by putting in the live dvd and booted it up in test mode.  I did not goto the install screen(s)  I also entered the commands you suggested (which is how I got to my old home folder).   Got any ideas as to how to get permissions (log in) ?  Oh, when I entered your commands, with the sudo, it did not once ask me to login.  This is strange?

If you did this from a live system you will need to open nautilus, the file manager, with command ```
gksudo nautilus
```and you will then be able to copy youir /home files and folders to the external drive.

What filesystem is the external drive formatted to, fat32, ntfs, ext#?

---

### Post by jgw on 2013-09-20
when I tried to run nautilus it told me that it could not set .config at the root so I had to set permission first.  
The external drive is formatted for windows but i've not had problems with that in the past.  I guess I could hook it up to another ubuntu machine are reformat if you think its necessary.

Here is what I did.  I wanted to save the TV folder (over 400gb be done tonight <g>)  anyway, ran nautilus from the terminal.  This cleverly brought up the home directory then mnt/test/heme/greg .   then I opened a new sheet for the the external drive.  I then went back to the tv folder and went to its properties.  Changed the user to live user and then changed all the properties to read and write, etc.  I then applied said properties and it worked!  Its currently copying 450+ files to the external drive <G> 
It should finish sometime tonight.  I also checked the external drive to make sure it was actually copying and IT WAS!

I should have put a usb 3.0 card into the machine but, I suspect, it wouldn't know what to do with it and I am not sure my hookup would have helped much either.  If I do get this stuff done then all I have to do is to simply install as new and ubuntu will take care of the rest (I am lazy which, I suspect, is one of the reasons for this happening in the first place)

I continue to wonder about the downloaded ubuntu 12.043.3    I have now downloaded it about 4 times and have written at least 3 dvd's, all for naught.  The last one came close (got the little icon, on the lower middle of screen) and then, a couple of minutes later, the machine quit sending any video and just stared at me.  I don't know which is worse, the windows blue screen of death or the black screen of ubuntu.  

Anyway, thanks!!!!!  (if you have any more thoughts let me know!  I will be interested!)

---

### Post by Bashing-om on 2013-09-20
jgw;

+ 10 ajgreeny's advise !

What pops to mind is that the external device was not "safely unmounted" at some point .. what happens if you fire up Windows and attempt to access that external device from Windows .. and from Windows "safely unmount" the device ?

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by oldfred on 2013-09-20
One of your issues is this:

> Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1953520064   976760001   42  [COLOR=#ff0000]SFS[/COLOR]

The SFS is for dynamic partitions. You get that from Windows as a proprietary overlay over physical partitions when you use MBR and want more than 4 partitions. It usually does not use the extended with logical partitions. It is somewhat like LVM is in Linux. 
You can use Windows tools to convert back as long as you have not created more than the 4 primary partitions on sda, so the logical match the physical.
If you have no data to recover from the NTFS partition then just delete it, but I do not think most Linux tools will do that.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

A couple of users have also used testdisk to undo dynamic but it is a bit more risky.
      
 Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

---

