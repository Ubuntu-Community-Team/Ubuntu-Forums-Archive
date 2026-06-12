---
title: "Windows bootloader"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by abward on 2007-09-27
I just installed 7.04 on my machine, and I am trying to set up for dual boot, using the Windows XP bootloader.

I followed these instructions: [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=1)

I set everything up and selected Ubuntu in the windows bootloader. The screen flashed and the PC just reboots.

So, I looked in the ubuntu.bin file that I create with the dd command, per these instructions.  It is 512 bytes, but there is nothing in there.  I recreated the .bin file again, and the dd command appears to be running correctly, and reports that it wrote 512 bytes, but again the file is empty.

I am doing this from my ext3 partition, which has a /boot/grub folder in it.

Is this file supposed to be empty?  What am I doing wrong?

Windows still loads, so I have not screwed anything up, yet.

Thanks

---

### Post by Pumalite on 2007-09-27
You would have better luck and performance if you installed Ubuntu to its partition and Grub to the MBR. It does it automatically and by default. You end up with a menu to boot either OS.

---

### Post by abward on 2007-09-27
Thanks, I will keep that in mind, if I cannot get this to work.

I do want to try and get this to work with the Windows bootloader first.

---

### Post by jbuc89 on 2007-09-27
I'm using the Windows boot loader to load Grub and then boot into Ubuntu.  Works just fine and no messing with the MBR and grabbing the XP CD to run fixmbr when Grub overwrites the mbr.

I would check your Grub installation to make sure it is pointing to the correct Linux partition as Grub starts its numbering at 0 (kind of confusing).

This is taken from /boot/grub/menu.lst

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=583578bf-99f4-4b37-8db4-13b882801cc7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

The root (hd0,6) command tells Grub I have it installed on the 1st hard drive and the 7th partition.

As a side note, I have a rather old BIOS and experienced a terrible problem getting Grub working as the BIOS only recogized the first 135 GB of my 250 GB drive and I was trying to create the EXT3 partition after 135GB. I needed to make sure the Ubuntu partition was installed in the first 135 GB.  I think it is a Grub/BIOS issue. The entire 250 GB is recognized by both Windows and Ubuntu after installation.

---

### Post by abward on 2007-09-27
Here is my menu.lst:
=============================
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fb03e180-3098-4b39-baae-d04233905379 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fb03e180-3098-4b39-baae-d04233905379 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1
====================

I tried changing the Linux entries to (hd0,1), since ext3 appears to be my second partition on the first drive, but no difference.

I still think the empty .bin file is fishy.  Is your .bin file, that the windows loader points to, empty too?

BTW, I have a new, modern motherboard, with SATA drives.

---

### Post by abward on 2007-09-27
I looked at the .bin file with SlickEdit and turned hex on.  The entire 512 bytes are all 00 hex.  This does not seem correct to me.

---

### Post by jbuc89 on 2007-09-27
There is actually a ton of posts on the subject.  Just do a forum search for ntldr linux and you will find lots of users dual booting this way.  I think it is the preferred method for Windows users experimenting with Linux.

The file is not empty but it is a image file of the first 512 bytes of the partition where grub is installed.  You probably wouldn't see anything if you opened it up with a text editor.  Basically it hands off the Grub boot process to the partition where grub is installed.  Unfortunately, when I was having my problems just a GRUB prompt showed up.  I ended up installed Grub for Windows and Grub for DOS in frustration and one of those programs eventually led me to my partition not found problem.

Just clarify my last post, i ran the following command

sudo dd if=/dev/hda7 of=bootsect.lnx bs=512 count=1

and then copied the bootsect.lnx file to my Windows boot partition and modified boot.ini.

Here is my output from

sudo fdisk -lu

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    43504019    21751978+   7  HPFS/NTFS
/dev/hda2        43504020   488392064   222444022+   f  W95 Ext'd (LBA)
/dev/hda5        43504083    45544274     1020096    7  HPFS/NTFS
/dev/hda6        45544338    47584529     1020096   82  Linux swap / Solaris
/dev/hda7        47584593    68067404    10241406   83  Linux
/dev/hda8        68067468    88550279    10241406   83  Linux
/dev/hda9        88550343   109033154    10241406   83  Linux
/dev/hda10      109033218   129516029    10241406   83  Linux
/dev/hda11      129516093   195045164    32764536    b  W95 FAT32
/dev/hda12      195045228   488392064   146673418+   b  W95 FAT32

I have one primary partition and have setup several EXT3 partitions in the extended partition to test different Linux distros on.  Ubuntu is on /dev/hda7 which corresponds to hd(0,6) in Grub speak.  I also put 2 large FAT32 partitions at the end of the extended partition as both Windows and Linux can easily read/write from them.

Hope this helps.

---

### Post by jbuc89 on 2007-09-27
Please post your output of

sudo fdisk -lu

Also here is a good Grub thread

[http://ubuntuforums.org/showthread.php?t=224351&highlight=re-install+grub+livecd](http://ubuntuforums.org/showthread.php?t=224351&highlight=re-install+grub+livecd)

---

### Post by jbuc89 on 2007-09-27
Also if you are using SATA drives, I think they are addressed by Linux as sda instead hda for the first drive.  What did you use for your dd statement?

sudo dd if=/dev/hda7 of=bootsect.lnx bs=512 count=1

Might need to be /dev/sda(partition number)

---

### Post by abward on 2007-09-27
> **jbuc89 said:**
> Please post your output of

sudo fdisk -lu

Also here is a good Grub thread

[http://ubuntuforums.org/showthread.php?t=224351&highlight=re-install+grub+livecd](http://ubuntuforums.org/showthread.php?t=224351&highlight=re-install+grub+livecd)

Here is the output:

========================

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61448624    30724281    7  HPFS/NTFS
/dev/sda2       169212645   312576704    71682030    f  W95 Ext'd (LBA)
/dev/sda3        61448625   160826714    49689045   83  Linux
/dev/sda4       160826715   169212644     4192965   82  Linux swap / Solaris
/dev/sda5       169212708   312576704    71681998+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   261361484   130680711    7  HPFS/NTFS
/dev/sdb2       261361485   312576704    25607610    f  W95 Ext'd (LBA)
/dev/sdb5       261361548   312576704    25607578+   7  HPFS/NTFS

Disk /dev/sdc: 2014 MB, 2014838784 bytes
64 heads, 63 sectors/track, 976 cylinders, total 3935232 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             253     3935231     1967489+   6  FAT16

===============

Which tells me that it is the 3rd partition, so root (hd0,2) is correct in the menu.lst.

---

### Post by abward on 2007-09-27
> **jbuc89 said:**
> Also if you are using SATA drives, I think they are addressed by Linux as sda instead hda for the first drive.  What did you use for your dd statement?

sudo dd if=/dev/hda7 of=bootsect.lnx bs=512 count=1

Might need to be /dev/sda(partition number)


The command I used was:

sudo dd if=/dev/sda3 of=/media/disk/ubuntu.bin bs=512 count=1

/media/disk is my USB pen drive.  And, the Windows boot.ini has:

C:\UBUNTU.BIN="Ubuntu Linux" on the last line.


I just tried it again, and I still get 512 bytes of all hex 00, and it still does not work.

---

### Post by jbuc89 on 2007-09-27
Being a Windows guy I'm probably outside my area of expertise now. ;-)

Did you check to see if Grub was installed correctly?  From the link I gave you with the Grub information, you can check to see if it finds Grub (these commands are from the grub link, jusk make sure you don't write to the MBR e.g. root (hd0) use root (hd0,?) where ? is your partition.

Boot into the Ubuntu Live CD. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter.

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the partition

Code:

setup (hd0,?)

Finally exit the grub shell
Code:

quit

---

### Post by abward on 2007-09-27
OK, I followed those steps to install it at (hd0,2), as reported by the find.  Still did not work.

Me: 0, Linux: 1

I have thrown in the towel and reformatted the ext3 partition and did the install again,letting it install grub  on hd0.  After all, I just need to run fixmbr from the XP boot disk to go back, if I want.

Working fine so far.

Thanks for all your help!

---

### Post by jbuc89 on 2007-09-27
Sorry you scratched using ntldr.  Did you re-run the sudo dd command after re-installing Grub?   Oh well, maybe next time. 

I think I ended up re-installing Ubuntu too and just used the Advanced button on the very last install screen where it tells you the changes it was going to make and had it install Grub at hd(0,6). 

Before rebooting, I ran the sudo dd command and then just used one of my FAT32 partitions to copy the bootsect.lnx file from my home directory.  Also, before rebooting after the install I ran the Grub find command to make sure it could find Stage1.

I booted into Windows copied over bootsect.lnx from the FAT32 partition to my NTFS Windows boot partition, modified boot.ini and I was in business.

I'm getting ready to install Mandriva Spring 2007 on one of my other EXT3 partitions.  Guess I will see how that goes.

---

### Post by Pumalite on 2007-09-27
> **abward said:**
> OK, I followed those steps to install it at (hd0,2), as reported by the find.  Still did not work.

Me: 0, Linux: 1

I have thrown in the towel and reformatted the ext3 partition and did the install again,letting it install grub  on hd0.  After all, I just need to run fixmbr from the XP boot disk to go back, if I want.

Working fine so far.

Thanks for all your help!

Glad you got it to work1

---

