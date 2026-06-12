---
title: "[SOLVED] I'm 90% there; need dual boot magician please."
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by stevelasvegas on 2007-09-07
Ultimately I want to be presented with a menu that will allow me to choose which o/s I want without any user input. So the computer boots into the menu and that Windows be the default o/s which it will automatically select after X seconds.

The reason I need this functionality, is that I leave my computer off and I access it remotely by powering it up using wake on lan. So it has to go from power up to Windows login screen all by itself.

Now I can boot in to either Windows or Ubuntu by selecting the proper Disk in the bios. I am guessing that I could continue this method (not my first choice) or modify the Windows boot.ini (although I don't know what the added information to point to Ubuntu would be) or boot to the Ubuntu Disk and modify the Grub menu (I have no idea how to modify that).


Here are some details:


**Here is what it looks like in Windows (boots from C: 2 drives raid 0**
[IMG]http://farm2.static.flickr.com/1131/1332780091_796c602e14.jpg?v=0[/IMG]

**and here is what is looks like in Ubuntu**
[IMG]http://farm2.static.flickr.com/1263/1332779921_2be1cd23d6.jpg?v=0[/IMG]

---

### Post by banewman on 2007-09-07
You can set this up from ubuntu by editing the /boot/grub/menu.lst file. From a terminal type - sudo gedit /boot/grub/menu.lst - give your password and gedit will bring up the file in a manner that allows you to save your changes. The first line without a "#" at the start is "default=0". This is the default os that gets booted if you don't make a selection at the grub menu. Remembering to count the first entry as zero - i.e. 0,1,2... - count the entries down to windows in your grub menu. If windows is the fourth one - don't count the "other op..." entry - then change the default entry to 3. Save the menu.lst file and reboot to check. Hope this helps. :)

---

### Post by stevelasvegas on 2007-09-07
Yeah, I get the display part. The part I don't understand this part:
# title        Windows 95/98/NT/2000
***# root        (hd0,0)*** <---- This part
# makeactive
# chainloader    +1
# 

What information can I give you (other than the images above) that will tell us what to put here so it will find the Disk(s) (my C: drive in windows consists of 2 physical hard drives ~74 GB each, raided 0) and boot Windows?

---

### Post by stevelasvegas on 2007-09-07
I have another Windows machine that I installed Ubuntu on that during the installation process, it apparently recognized that Windows was on that machine and it automatically created a dual boot menu. How did that create the dual boot menu so easily and getting an answer to creating a dual boot manually on this machine is so difficult?

---

### Post by banewman on 2007-09-07
Apologies. I thought you had both options - to boot into ubuntu or windows - at the grub menu. In the file - /etc/fstab - there will be a listing of the mounted partitions that grub has recognised. Is your windows partition listed?

---

### Post by stevelasvegas on 2007-09-07
No need for apology necessary. I appreciate the time you are giving me.

This is what the file shows:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1d1ff05e-8211-4fd7-8c96-a16bc285bd2e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=2f515d92-d22d-451d-9326-085256654f45 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by banewman on 2007-09-07
From the fstab file it looks like you added windows after ubuntu. Is that the case? If it is it is hard to get grub to mount the partition because it allocates UUID numbers to partitions it sees in order to mount them. I would like to know if you get any entries in the grub menu at boot apart from the two kernels and memtest - the lines from menu.lst that you copied earlier I think are from the example part of that file - they have the "#" comments in front of them. The OS entries are right down the bottom. :)

---

### Post by stevelasvegas on 2007-09-07
Windows was installed 1st. There are no other listings in the Grub menu.  Here is my menu.lst in boot/grub.
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1d1ff05e-8211-4fd7-8c96-a16bc285bd2e ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1d1ff05e-8211-4fd7-8c96-a16bc285bd2e ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1d1ff05e-8211-4fd7-8c96-a16bc285bd2e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1d1ff05e-8211-4fd7-8c96-a16bc285bd2e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIS

---

### Post by merlinus on 2007-09-07
PMFJI, but perhaps part of the problem is in which of your hdds is set to boot first?

Also, post results of:

```

sudo fdisk -l
blkid
mount

```

because according to your gparted screen shot, something seems amiss, as well as /boot/grub/menu.lst.

-merlin

---

### Post by banewman on 2007-09-07
My question now is in your first post the partition display from both windows and ubuntu show no primary partition from windows which is hard to accomplish. How did you go through the process of installing both OS's? Maybe that will help us get you to a dual boot. :)

---

### Post by stevelasvegas on 2007-09-07
I don't know what 'PMFJI' means.
If I understand ' which of your hard drives boots first' means;
I set which drive boots in the bios, right now. If I boot to the drive that has Windows on it (my C: Drive which are 2 physical sata drives raid0 together) or the Linux drive. A partition on another physical sata  drive. But this method of booting into each operating system by choosing the boot drive in the bios, is what I am trying to get away from. Ideally, I want to boot the the Linux partition and use GRUB to present a menu. Else, I will try to use a boot utility on the Windows side to present a menu. But I have heard that Grub is a more reliable way to configure such a menu as opposed to messing with boot.ini & NTLDR stuff in Windows.

```
**steven@Fatal1ty-Ubuntu:~$ sudo fdisk -l**
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       58862   472800982+   f  W95 Ext'd (LBA)
/dev/sda2   *       58863       60801    15575017+  83  Linux
/dev/sda5               2       25498   204804621    7  HPFS/NTFS
/dev/sda6           25499       58771   267265341    7  HPFS/NTFS
/dev/sda7           58772       58862      730926   82  Linux swap / Solaris

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18078   145211503+   7  HPFS/NTFS

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36483   293049666    7  HPFS/NTFS

Disk /dev/sde: 520 MB, 520093696 bytes
16 heads, 32 sectors/track, 1984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        1984      507888    b  W95 FAT32

Disk /dev/sdi: 1017 MB, 1017643008 bytes
29 heads, 60 sectors/track, 1142 cylinders
Units = cylinders of 1740 * 512 = 890880 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1        1143      993667+   6  FAT16
```
[B]
steven@Fatal1ty-Ubuntu:~$ blkid[/B]
```
/dev/sda2: UUID="1d1ff05e-8211-4fd7-8c96-a16bc285bd2e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="ntfs" 
/dev/sda6: TYPE="ntfs" 
/dev/sda7: UUID="2f515d92-d22d-451d-9326-085256654f45" TYPE="swap" 
/dev/sdd1: TYPE="ntfs" 
/dev/sde1: LABEL="TESTING" UUID="B8AA-EE10" TYPE="vfat" 
/dev/sdi1: SEC_TYPE="msdos" UUID="3417-28A9" TYPE="vfat" 
[B]```

steven@Fatal1ty-Ubuntu:~$ mount
```[/B]
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdi1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sde1 on /media/TESTING type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

---

### Post by stevelasvegas on 2007-09-07
It looks to me (but then I don't known much about this) that the below are my (2) 75GB hard drives that are raid 0 together to form my C: drive that windows boots from.

/dev/sda5 2 25498 204804621 7 HPFS/NTFS
/dev/sda6 25499 58771 267265341 7 HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

---

### Post by stevelasvegas on 2007-09-07
This is how I got Linux installed on my existing Windows machine.

This is an excerpt from a previous thread when I was getting help on the installation:
In this case the easiest way is to use windows, delete the Linux partition, then create a partition of 261000MB (do not bother formattaing it), this should leave about 15GB unallocated. Then in Ubuntu select: "Use the largest contiguous free space".

Complete conversation in previous thread:
[http://ubuntuforums.org/showthread.php?t=542191](http://ubuntuforums.org/showthread.php?t=542191)

---

### Post by merlinus on 2007-09-07
You may wish to investigate this:

[http://www.snapfiles.com/get/easybcd.html](http://www.snapfiles.com/get/easybcd.html)

-merlin

---

### Post by banewman on 2007-09-07
Was having an interesting time reading your fdisk output!  The problem of no dual boot seems to stem from your partition setup. You need a primary partition for windows, then an extended partition for any other seperate windows partitions you want. A primary partion for "/" or "/boot"  and an extended partition for whatever else you want to seperate. I have a primary partition for "/", an extended partition with "/opt" and "/home" on seperate partitions. To get a dual boot going you will need to start again with your partitions, I'm sorry to say.
You have ntfs, fat32, fat16 ... why? How did that happen? :)
Pardon Me For Jumping In - pmflji - hehe

---

### Post by merlinus on 2007-09-07
Ubuntu can live on primary or logical partitions.  Windows needs to be on a primary, and clearly prefers to be first.

-merlin

---

### Post by banewman on 2007-09-07
Trying to be totally sure we get a dual boot for Steve here. Belts and braces kind of approach seems the safest. :)

---

### Post by stevelasvegas on 2007-09-07
***To get a dual boot going you will need to start again with your partitions, I'm sorry to say.***

Meaning reinstall of Linux only or Windows also?

---

### Post by stevelasvegas on 2007-09-07
I believe the Fat32 & Fat16 partitions are;
Fat32 = a 1GB thumb drive
Fat16 - a 1GB CD card
Both plugged in through USB ports

---

### Post by banewman on 2007-09-07
Well, just reinstalling windows won't give ubuntu's grub an oppurtunity to recognise it and you do have what seem to be unneeded fat32 + fat16 partitions. Being the neat freak that I am I would tidy the job and make it functional with a back up of all necessaries and a full format and reinstall. That is your call but from your fdisk output it seems a new approach needed. :)
Your last post came as I was typing this one. :)

---

### Post by merlinus on 2007-09-07
Just on the offchance -- have you tried booting without those external drives?

-merlin

---

### Post by banewman on 2007-09-07
Because ubuntu's grub didn't see the windows partition and windows won't recognise a linux partition the only option I see is a reinstall for ubuntu. But you may have the same problem again with windows not being on a primary partition...

---

### Post by stevelasvegas on 2007-09-07
[IMG]http://farm2.static.flickr.com/1348/1342563853_342008b481.jpg?v=0[/IMG]

---

### Post by banewman on 2007-09-07
Steve, I'm sorry to say, but if you look at the lines there they say windows is in an extended partition. Not anything a person wants to hear, that a reinstall is needed to get what they want. Apart from the above suggestions I don't know anything else to suggest. Keep going like you are...
To partition properly is one of the learning curves with linux because nearly everyone starts out dual booting but have never had to do it before. Windows is normally a one partition install. Take heart, most have been in your shoes before. :)

---

### Post by merlinus on 2007-09-07
It may be because I am more than halfway around the world from Brisbane, but...  it sure looks to me that his windows install is on his second hdd, and on a primary partition.

Also looks like the first hdd has two ntfs partitions, neither of which appears to be the windows install.

-merlin

---

### Post by banewman on 2007-09-07
I'm looking at types in the first post. How can you have an unallocated partition that is primary?
And look at status....
Apologies. Disk 2 shows an active ntfs file system.
But with no UUID there is not a way that I know to get ubuntu's grub to recognise the windows partition.

---

### Post by merlinus on 2007-09-07
I completely agree that steve's first hdd seems totally fscked.  :)

But are uuids necessary for ubuntu to recognize the windows install partition?  I know they are not for other ntfs partitions, so that is why I am asking.

-merlin

---

### Post by banewman on 2007-09-07
If you look at fstab the lines with sda etc are commented out - it uses the UUID to mount the partition. Without those I don't know a way to force a mount. Do you?...:)

---

### Post by merlinus on 2007-09-07
/dev/sdb1 /media/sdb1 ntfs defaults,locale=en_US.UTF-8,umask=0002 0 2

---

### Post by banewman on 2007-09-07
That's not in Steve's fstab. Is it in your's?
Without a "#" in front of it?

---

### Post by merlinus on 2007-09-07
NTFS drives can be mounted this way, manually or in /etc/fstab.

But this in no way solves the problems with the messed-up partitions on his first hdd.

And his /etc/fstab posted way back on the first page of this thread does not list any ntfs partitions, so clearly ubuntu is not referencing his second hdd.  

Maybe the raid setup is causing this.  I have seen a number of threads detailing problems with this and ubuntu.

-merlin

---

### Post by Herman on 2007-09-07
What an interesting thread!  :popcorn:

 :) stevelasvegas, Why not give [GAG Boot Manager]("http://gag.sourceforge.net/") a try?  It's only a small download and you can test it out on a floppy disk first to see if it will help of not. Here's more info on GAG as it relates with Ubuntu,  [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")  GAG Boot Manager, a Windows and Linux booting alternative.

If you were able to boot both OSes from your BIOS they must at least be bootable. (Although it is unusual for Windows to boot in a logical partition, you need to be a bit clever to accomplish that) here's a link about booting Windows in a logical partition,  [    Understanding MultiBooting and Booting Windows from an Extended Partition]("http://www.goodells.net/multiboot/index.htm") by Dan Goodall.

GRUB does support5 RAID, here's a link, [http://grub.enbug.org/LVMandRAID](http://grub.enbug.org/LVMandRAID)

Here's a few links about Ubuntu and RAID installs, [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[http://ubuntuforums.org/showthread.php?t=413647&highlight=grub](http://ubuntuforums.org/showthread.php?t=413647&highlight=grub)

[http://ubuntuforums.org/showthread.php?t=421405&highlight=grub](http://ubuntuforums.org/showthread.php?t=421405&highlight=grub)

[http://ubuntuforums.org/showthread.php?t=430181&highlight=grub](http://ubuntuforums.org/showthread.php?t=430181&highlight=grub)

and here's one more link about RAID (hardware RAID), in case it helps at all, [http://www.adriansrojakpot.com/Speed_Demonz/IDE_RAID/RAID_01.htm](http://www.adriansrojakpot.com/Speed_Demonz/IDE_RAID/RAID_01.htm)

I don't know much about RAID or LVm myself, I have never tried it out. I was thinking about it for a while just to see what I can learn to try to help in this type of situation, but there are so many different kinds of RAID, it would be a very time consuming job to test tehm all and find  out all about them.

What we need more LVM and RAID users here who can stick around help, other RAID and LVM users. :)

Regards, Herman :)

---

### Post by merlinus on 2007-09-07
Thanks for chiming in, Herman!  I am sticking around because if this can be resolved without a reinstall, I will have learned a lot....

It does seem, however, that his windows install, on sdb1, is on a primary partition.  And if he can boot into one or the other os, but not both, I wonder if it may be related to BIOS settings, cabling, or such?

-merlin

---

### Post by Pumalite on 2007-09-07
I've been following this thread too and my question is: can the Raid Array be in the middle of all this? I'm a newbie compared to others in this forum, but Ubuntu is installed in another drive, nevertheless, it seems to me, the installation of Grub has to deal with the Raid Array

---

### Post by banewman on 2007-09-07
Been doing some reading and need Steve to answer on the age of his comp and if in bios there are any settings to deal with raid?
STEVE, help us out here. can you tell us if the comp has raid settings in bios?:)

---

### Post by stevelasvegas on 2007-09-07
Yes, the Raid settings are in the bios. I will get a couple of screen shots that will display this information.

---

### Post by stevelasvegas on 2007-09-07
Here is where I select which disk to boot from in the bios.
If I select SCSI-2, I boot into windows. SCSI-2 is comprised of (2) 69gb SATA drives connected with sata cables.
If I select SCSI-0, I boot into Ubuntu. This drive is a SATA2 drive I recently installed. I am using (2) NTFS Windows partitions to use with Windows. Then I installed Ubuntu using the Live CD and partitioned 15gb at the end of that drive to house Linux, (utilizing the largest contiguous free space as detailed in previous post)  It was partitioned during the Ubuntu installation.
[IMG]http://farm2.static.flickr.com/1029/1343892830_6c9c4c99c0.jpg?v=0[/IMG]

This is the Raid setup screen. I access it by sending a ctrl+I during the bios boot before Windows starts to boot.
Physical Disk:
Port 0 = SCSI-0 stated above
Port 1 and port 2 are the 2 hard drives that are referred to above as SCSI-2
Port 3 is irrelevant, just another hard drive that I use to store my backups.
[IMG]http://farm2.static.flickr.com/1140/1343892848_e815da5e69.jpg?v=0[/IMG]

The computer is 3 years old and the motherboard is a Abit Fatal!ty AA8XE

---

### Post by banewman on 2007-09-07
This is teaching me lots about raid setups for when I eventually setup my own system with them. thanks. Now, to relevant matters. When you installed ubuntu was there an option as to where you put the grub bootloader or the mbr or something like that? The reason I ask is if you put grub on what would be your third disk that might be part of the problem. I can't recall getting that option but I use 1 disk per comp.

---

### Post by stevelasvegas on 2007-09-07
Banewman,
Take a look here when I did the Ubuntu installation. You will see what installation options that were presented to me and what steps I followed with help from AGO (another helpful user).

Complete conversation in previous thread:
[http://ubuntuforums.org/showthread.php?t=542191](http://ubuntuforums.org/showthread.php?t=542191)

---

### Post by Sef on 2007-09-07
RE: Post 23

Shouldn't Windows be set as the boot?  In the picture, it seems that Linux and the swap are set as the boot. (They are both starred.)

---

### Post by banewman on 2007-09-07
As I understand it, Sef, Steve is looking for a grub option to set windows as the default instead of using the bios as he has to at the moment. Problem is, fstab has no UUID for the windows partition....

---

### Post by banewman on 2007-09-07
Steve, when i installed Mephis,suse and Knoppix, they gave me the option to install grub in their partition or the first part of the first disk but I have never had that option with ubuntu from hoary to feisty. If you have a live cd put it in and run it. Then go to terminal and we will try to install grub to the first partition if it isn't there already. At terminal type - sudo grub <enter>
                                                                                                            find /boot/grub/stage1<enter>
and the output of that tells us where to go .....
Steve, disregard this as there is no UUID for your windows partition so I couldn't tell you which direction to head in after finding your grub's location. Sorry if your working on it already...:)

---

### Post by Pumalite on 2007-09-07
Feisty, during installation gives you the option to install Grub wherever you want in step 7, through the 'Advanced' tab.

---

### Post by banewman on 2007-09-07
Pumalite, I hope you'll notice I said "gave" me the option, that is different to hiding it from novices - I don't know the default but since I have had no issues with it I asume it is (hd0)...?:)

---

### Post by merlinus on 2007-09-07
@banewman --

Looks like you are still insisting that there has to be a uuid for the windows partition.  Sorry, but I have no problems mounting any ntfs partition, with or without a uuid.

The only reason to use uuids might be if partitions and drives keep changing order.

Perhaps you can point me to some documentation that says otherwise?

-merlin

---

### Post by banewman on 2007-09-07
Merlin, have you looked at your post #31? As I said earlier if you look at fstab the lines not corresponding to UUID's are commented out. If, with ntfs, this is not an issue, tell Steve - I gave up windows in 2002, have never used ntfs and am just trying to work through an issue a bloke is having and no-one else would help with. If you know how to mount a ntfs partition that is not in fstab you have one up on me and I ask you to share that with the person who started this thread and has the problem, Steve. :)

---

### Post by merlinus on 2007-09-07
I did, in post #29 in this thread.

Ubuntu wants to use uuids, and that is why the # in front of the lines using them in /etc/fstab, but they are not necessary unless, as I said, partitions and drives keep changing.

Then uuids are wonderful for identifying these without the problems caused by sda1 becoming sdb1 and such.

In fact, in a recent situation, the uuids being returned by blkid actually created problems for the user when mounting partitions, because for some reason they were incorrect.  Using the method I suggested helped to solve the problem.

-merlin

---

### Post by banewman on 2007-09-07
Great! Tell Steve how he can mount his windows partition and have grub select it as the default. That's why we are here. Glad you could get another ubuntu user with problems back on the right track. :)

---

### Post by merlinus on 2007-09-07
Steve --

Let's see if we can manually mount your windows partition.

```

sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1[SIZE=3] [COLOR=black]-t ntfs -o nls=utf8,umask=0222[/COLOR][/SIZE]

```

then:

```

sudo umount -a && sudo mount -a

```

Navigate to Places/Computer/FileSystem/media and see if sdb1 is there.

-merlin

---

### Post by merlinus on 2007-09-07
Also, check confused57's post in your original thread:

[http://ubuntuforums.org/showthread.php?t=542191&page=3](http://ubuntuforums.org/showthread.php?t=542191&page=3)

---

### Post by stevelasvegas on 2007-09-07
Here's what happened when I followed post #50:

```
steven@Fatal1ty-Ubuntu:~$ sudo mkdir /media/sdb1
```
Password:
```
steven@Fatal1ty-Ubuntu:~$ sudo mount /dev/sdb1 /media/sdb1 -t ntfs -o nls=utf8,umask=0222
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Pumalite on 2007-09-07
That's because sb1 is part of the Raid Array.

---

### Post by merlinus on 2007-09-07
What happened with following confused57's suggestion?

@Pumalite:  The Raid Array sounds like the last part of your sig.

-merlin

---

### Post by Pumalite on 2007-09-07
What about following Herman's suggestions and link's?.

---

### Post by stevelasvegas on 2007-09-07
I followed Confused instructions:
You need mapping lines to boot Windows on a 2nd hard drive:
Code:

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

And now I am presented with a Grub menu that includes Windows XP.
It actually boots into Windows XP and it also boots into Ubuntu when I select that. I think we've done it Ole!
Now I can massage Grub to delay and display and select the default OS.
Could this possibly be the end of the thread or is there something else I need to be aware of. Either way, for me this is the beginning of learning WHY this worked.

I will post this in the other thread where this all began.
Thanks, all of you for all of your time and efforts.
Especially Confused57 - hip hip hooray!
I think we all win if we follow the path I have taken and learn all we can from this well participated project.
Again, thank you all so very much. I hope I am able to gain knowledge and in the future help someone else realize the great feeling it is to work with such an excellent community.

---

### Post by Pumalite on 2007-09-07
@Pumalite: The Raid Array sounds like the last part of your sig.

-merlin

Hey Merlin, I'm glad that confused57 showed his mettle again and fixed this, but you are right; in my opinion Raids are a waste of time: Raid0=minimal performance improvement; Raid5=going around with suspenders and a belt and nothing to show for it.
(Unless you are going to use a real hardware Raid; don't waste your time)

---

### Post by banewman on 2007-09-07
Hey Steve, very happy for you! :lolflag:

---

