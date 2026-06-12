---
title: "HOWTO: Backup a Partition"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by IgnorantGuru on 2007-02-13
[COLOR="Red"]EDIT:[/COLOR] I have also made a Wikibooks guide which covers this topic in greater detail: [http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)


After reading some of the problems folks have had with updates/upgrades, I thought I would share my method for backing up partitions and maintaining a multi-OS system.  I'm sure there are other approaches but this has worked well for me.

Basically this procedure allows you to backup an entire partition (your Ubuntu or WinXP installation, for example) to one "partition image file".  This image file can be stored on another partition, another drive, a networked filesystem, or burned to a CD/DVD.  If something goes wrong with the system, due to any kind of system problem, bad upgrade, or hard drive failure, you can just roll the system back to the exact state it was in when you saved the image - restoration takes 5-10 minutes.

I have found having a reasonably recent image of my partition takes the worry out of testing new updates, messing with drivers, or trying a new version of the OS.  If anything goes really wrong, just roll it back.  Also, if I'm working on something and the computer goes haywire, rather than having to stop what I'm doing and spend hours straightening it out, I just restore it in 5 minutes.  It is very good for WinXP too, where network settings can mysteriously gunk themselves.  Rather than trying to find what went wrong, I just roll it back to when it did work.  Finally, it's a good test of hardware.  If the problem still exists after restoration, you know it's probably a hardware issue.

In short, it's well worth spending a little time learning how to do this!

Works with ext2/3, reiser, FAT32, and NTFS partitions.

First I'll give you my recommendations for setting up a hard drive.  You can backup any partition, but you need another place to store the backup.  The backup image file will be about half the size of the data on the partition (it is gzipped).  My image file of Kubuntu Edgy is 1.0GB.

If you're starting from scratch, I recommend a hard drive setup something like this:

```

device  size    mount       use
------  ----    -----       ---
hda1    2G      swap        linux swap
hda2    5G      /           kubuntu (reiser or ext3)  [boot partition]
hda3    7G      /mnt/winxp  windowsxp (fat32 or ntfs)
hda4    xxG                 Extended
hda5    7G                  extra system
hda6    5G      /home       user configs (reiser, ext3)
hda7    xxG     /data       user data (reiser, ext3, or fat32)
```

The swap partition should be at least double the size of your RAM.

Ubuntu usually fits comfortably in 5G (my 5G partition is 55% full).  If you are going to install a lot of large software, then make it bigger.

The "extra system" partition is good to make for later.  This is a place where you can install a new OS to try it out, without affecting your other OSes.

Making a separate partition for /home is one approach.  /home is where Ubuntu stores all your user settings, like gnome/kde/software preferences and settings, etc.  Having it on a separate partition means that when you roll back the system partition, the user settings are unaffected.  You can also skip the separate partition for /home and just make frequent backups of that folder.  If you need to roll back the system, you would then follow that by restoring the /home folder from your backup.

The /data partition is for anything else.  It's also a good place to initially store the backup image file(s).

To set up a drive like this, you can select 'manually edit the partition table' during Ubuntu install.  If you want XP on the system, it's easier to partition the drive first, then install XP to the appropriate partition, then install Ubuntu.  In that case you can use cfdisk to do the partitioning before the XP install (see below).  (The reason for installing XP first is that it overwrites the MBR and doesn't see Ubuntu, whereas when you install Ubuntu after XP, it sees XP and enables the multi-OS bootloader.)

GET SYSTEM RESCUE CD

SystemRescueCD is what I use to maintain the system and make backups.  This can be downloaded from [http://www.sysresccd.org](http://www.sysresccd.org) as an ISO file and burned to CD.  This creates a bootable CD.  SystemRescueCD is a slim linux liveCD with a bunch of system maintenance tools on it.  The new version even allows you to startx and run Firefox, but the command line tools are what we want.  SystemRescueCD has run successfully on every system I have ever used it on (unlike more complex LiveCDs).

Boot the SystemRescueCD.  Press Enter at the Boot and Keyboard prompts.  Eventually it will stop at a root console.  If you want to access the ethernet/internet, you may need to type net-setup.

cfdisk is one of the utilities you can run.  This allows you to (re)partition your hard drive.  Just be aware that this is a destructive process.  You can also startx and double-click the icon for GParted, which allows you to resize partitions non-destructively.

HOW TO BACKUP A PARTITION

Once you have your OSes installed and configured, make partition backups of each.  In fact, I often make several backups during installation (initial install, prior to installing the video driver, etc).  It takes a few minutes but saves time when things don't go as planned.

Boot SystemRescueCD.  First you need to decide where you want to save the backup image file.  If you want to save it on another partition, you need to mount that.  For example
```
mkdir /mnt/h7
mount /dev/hda7 /mnt/h7
ls /mnt/h7
```

Or, you can mount an NFS or Samba network share.  For Samba (windows shared folder):
```
mkdir /mnt/smb
mount -t smbfs -o lfs //192.168.10.3/my-share/ /mnt/smb/
```

It's also possible to mount a USB stick or external hard drive for this purpose.

Note:  The older version of SystemRescueCD could not mount an NTFS partition for writing.  I have not tried this, but the newer version claims to be able to do this with:
```
mkdir /mnt/ntpart
mount -t ntfs-3g /dev/hda3 /mnt/ntpart
```

Once you have mounted the partition or network share where you will save the image file, enter:
```
partimage
```

This will run the Partimage program, which is what makes the backup of partitions, and also restores them.

First, use arrow keys to select the partition you want to backup (in this example, hda2, or the kubuntu partition).  Then press Tab move the cursor to the filename field.  Assuming we mounted /mnt/h7 above, you might save the image file as:  /mnt/h7/image-kubuntu1 (this will place it in /data)

Now move down and make sure the 'Save partition to image file' option is checked (use space bar to select it).  Press F5 to proceed.  Next you are given some options - set these as you wish.  If the image file is larger than the set size (default 2G), it will be broken into multiple files (.000, .001, etc)  If you are saving the image file to FAT32 be sure to set this no higher than 4G.  Press F5 to proceed.

The partition will be gzipped and saved to the image file(s) - takes 10-15 minutes.  When it's done, exit partimage and umount whatever you mounted:
```
umount /mnt/h7
```

Now enter
```
reboot
```
When the screen goes blank, remove the CD so the computer boots into your OS.  You should now find the image file image-kubuntu1.000 where you saved it.  It will be owned by root - change this as you like.

First thing I do is create a text file image-kubuntu1.txt that describes the image (what version OS, what was installed on it, MD5SUM of the file, etc).  As I make changes to the system, I record them in this file.  If it's necessary to roll the system back, I then have a record of what changes I made since the image was made.

You can also burn this image file to DVD for safekeeping.  Although not necessary, it's possible to burn a copy of SystemRescueCD that contains the image file on the same DVD.  Assuming image-kubuntu1.000 is in the folder /data/mydvd-data-files/:
```
growisofs -Z /dev/hdc=systemrescuecd-x86-0.3.2.iso
growisofs -M /dev/hdc -J -R /data/mydvd-data-files/
```

If you want to burn the image file to a CD rather than DVD, then you should probably have partimage break the image into files no larger than 700M for you.


HOW TO RESTORE A PARTITION

If for any reason you want to roll the partition back, you follow similar steps.

First, boot SystemRescueCD and mount the partition or network share where the image is saved, in our example:
```
mkdir /mnt/h7
mount /dev/hda7 /mnt/h7
ls /mnt/h7
```

Or, if you burned the image file onto the SystemRescueCD DVD as shown above, you will find it in /mnt/cdrom.

Or, if your image is saved to another DVD or CDs, and you have only one CD/DVD drive, you will need to copy the files to a hard drive partition or network share before booting SystemRescueCD.  (The manual also says it is possible to issue a command and remove the SystemRescueCD from the drive, but the one time I tried this with an older version it did not work for me - your results may vary.)  [color=red]Update: If you enter "fb1024 docache doeject" or "fb800 docache doeject" at the Boot: prompt the CD will eject after booting.[/color]  If you plan to store your image files this way, you may want to store them on some kind of bootable disc so that you can copy them to the hard drive easily, or have a bootable floppy.

Once you have your image file location mounted, run partimage.  This time select the partition to restore, press Tab and enter the name of the image file, in this example /mnt/h7/image-kubuntu1.000

Be sure to select the option 'Restore partition from image' below the filename (use space bar to select it).  Press F5 to continue.  The partition will be restored in about 5 minutes.

Exit partimage, umount whatever you mounted, and enter reboot.  Remove the CD and your computer will travel back in time.


IMPORTANT NOTES:

* Be sure to keep a separate image file (or set of them) for each computer you maintain.  Using the image file from one computer on another computer will generally cause problems, unless the hardware is exactly the same.

* partimage is still experimental at backing up NTFS partitions.  I have never had a problem, but it says that if the partition is highly fragmented it may not be able to save the backup.  If this is the case you will receive an error, and will know that the image file was not created successfully.  (Try defragging several times and chkdisk)  Once an image is created successfully, it should restore without problems.

* In my experience, partimage will not restore an image to a partition that is smaller than the original, even if the data would fit.  It will restore the image to a partition that is larger than the original (the fs grows).

* Your MBR is not part of the partition image, so if this is damaged, you will need to restore it or replace it.  It is possible to backup the MBR - see below.  Also, be mindful that the MBR contains the partition table, so if you change your partition table, this is stored in the MBR.  It is also possible to separately backup the partition table and the boot code in the MBR.

* If you have a hard drive failure, the procedure is:  install and partition the new drive (using cfdisk, for example), then restore the partitions using partimage (hopefully you saved a copy of your image files elsewhere).  Restore or replace the MBR (install grub, etc).  (One way to restore the MBR is to install Ubuntu, which will install grub, then when the installation is done restore the Ubuntu partition to its previous state.)


OTHER NOTES:

SystemRescueCD has a lot of other useful tools worth investigating, including Clam Anti-Virus, partition table and MBR backup, freedos, and memtest.  (Type freedos or memtest at the Boot: prompt to boot into these modes).

Here are my notes on SystemRescueCD - see the manual for details.

```
SYSRESCD 0.3 NOTES

BOOT
	freedos
	memtest
	ranish		like fdisk (untested)
	aida		hardware info
	dban		wipe hard drives completely
	ntpass		windows registry editor / password editor
	fb800		frame buffer (for qtparted - defunct?)

NETWORK
	net-setup eth0						recommended
	dhcpcd eth0							establish (alternate method)
	ifconfig							info
	ifconfig eth0 192.168.1.110			manual
	route add default gw 192.168.1.1	manual gateway setup

CLAMAV
	freshclam							update virus sigs
	mount /dev/hda1 /mnt/testpart
	clamscan -r /mnt/testpart			virus scan

GPARTED
	startx
	use menu or gparted

SFDISK (partition table backup) (untested)
	Make:  sfdisk -d /dev/hda > bak-hda
	Restore:  sfdisk /dev/hda < bak-hda

MBR BACKUP (untested)
	Backup:  dd if=/dev/hdx of=MBR-backup bs=512 count=1
	Restore:  dd if=MBR-backup of=/dev/hdx bs=512 count=1
	Backup Boot Code Only:  dd if=/dev/hdx of=MBR-backup bs=448 count=1
	Restore Boot Code Only:  dd if=MBR-backup of=/dev/hdx bs=448 count=1
	Install Grub:  grub-install /dev/hda

PARTIMAGE (command line method)
	partimage -z1 -o -d save /dev/hda5 /mnt/myhd/rescuefile

MOUNT
	mount -t smbfs -o lfs //192.168.10.3/my-share/ /mnt/temp1/	(samba)
	mount -t ntfs /dev/hda1 /mnt/temp1					(read-only)
	mount -t ntfs-3g /dev/hda1 /mnt/temp1					(read/write)

BURN DVD
To master and burn an ISO9660 volume with Joliet and Rock-Ridge extensions on a DVD:
	growisofs -Z /dev/dvd -R -J /some/files
To append more data to same DVD:
	growisofs -M /dev/dvd -R -J /more/files
To finalize the multi-session DVD maintaining maximum compatibility:
	growisofs -M /dev/dvd=/dev/zero
To use growisofs to write a pre-mastered ISO-image to a DVD:
	growisofs -dvd-compat -Z /dev/dvd=image.iso

BURN CD
	In order to get the identifier numbers of your device:
		cdrecord -scanbus
	To burn image:
		cdrecord dev=/dev/hdc -v filename.iso
	To create and burn image at speed 2:
		mkisofs -R -o cdimage.raw /tmp/master/tree
		cdrecord -v speed=2 dev=/dev/hdc cdimage.raw
	Erase CD:
		cdrecord blank=fast dev=/dev/hdc
	Multisession
		mkisofs -J -L -R -o cdimage.raw /tmp/somefiles/*
		cdrecord -v -multi -data dev=/dev/hdc cdimage.raw
		# Locate the start of the free space on the CD:
		cdrecord -msinfo dev=0,5,0
	     #0,1263     (example output)
		mkisofs -J -L -R -o cdimagi.raw -M /dev/hdc -C 0,1263 /tmp/somefiles/*
		cdrecord -v -multi -data dev=/dev/hdc cdimage.raw

```

---

### Post by ernstblaauw on 2007-03-23
Thanks for this guide! Is it necessary to restore the backup to the same hard drive? I mean: At this moment my Ubuntu is at /sda6. Maybe, I will restore it on /sdc1. Is that a problem? (Of couirse, I have to alter GRUB to boot correctly).

---

### Post by IgnorantGuru on 2007-03-26
No, you can restore the image to any partition on any drive, so long as the destination is at least as large as the original source partition.

Grub and fstab are usually the only things which need modifying.

---

### Post by Palypup on 2007-03-29
Thanks. Just tried to go through the same process a few days ago before I read this.
Couldn't get SysRes to save to another partition (not room for both) so gave up.

---

### Post by Roobert on 2007-03-30
Thanks for the great info, IgnorantGuru! I've used your method to successfully backup a few of my partitions, easy as pie. Thanks!!

---

### Post by ImpelGD on 2007-04-24
This will come in very handy - thanks IgnorantGuru. :)

---

### Post by THEBIGEYE on 2007-05-31
hi was wondering will this work for me. i want to move ubuntu to a diffrent  larger drive but not have to reinstall all my apps,  ie clean install so was curious to see if ican take this image and reinstall a clean os and open the image from there??

---

### Post by louieb on 2007-05-31
Very nice. Do you plan to add it to the Ubuntu wiki?  If not  I need some practice doing wiki edits. I think it should be add to this page.  [BackupYourSystem - Community Ubuntu Documentation]("https://help.ubuntu.com/community/BackupYourSystem#head-a071da4b7755c7dee7e90d65f8cb98991cadf42c")
:popcorn:

---

### Post by IgnorantGuru on 2007-06-01
> **THEBIGEYE said:**
> hi was wondering will this work for me. i want to move ubuntu to a diffrent  larger drive but not have to reinstall all my apps,  ie clean install so was curious to see if ican take this image and reinstall a clean os and open the image from there??

Hi - Not sure I follow you.  You don't really 'open' the image.  You just boot the rescueCD and restore the target partition using the image file.

In your case, you should be able to make an image file of your root Ubuntu partition using the procedure above.  Then partition your new drive and restore the image to a partition on your new drive (at least as large as your current root partition, or larger).

That will effectively move Ubuntu from the old drive to the new drive.  The only remaining issue is booting the new partition.  If you use grub, you can add the new Ubuntu partition to menu.lst.  Or, you can manually install grub on the new drive and make that the boot drive.

If you're not comfortable installing or modifying grub, here's a trick...  using the Ubuntu install CD to install a fresh copy of Ubuntu to your new root partition, and let the installer install grub to the new drive.  Once that is booting correctly, then boot rescueCD and restore the new partition from your image file (thus replacing the fresh install you just did with your old installation).

Finally, you'll need to modify /etc/fstab on the new partition (after you restore it) such that it accurately reflects the move.  (You can do this from rescueCD by mounting the partition and using the pico editor (or is it nano?))

HTH

---

### Post by IgnorantGuru on 2007-06-01
> **louieb said:**
> Very nice. Do you plan to add it to the Ubuntu wiki?  If not  I need some practice doing wiki edits. I think it should be add to this page.

I would appreciate it if you would put it on a wiki - I was wondering where a good place might be.  I'll be quite busy for a couple weeks but after that I'll be happy to help fine tune it.  Thanks!

---

### Post by roastbeef on 2008-02-01
I have a drive with 5 partitions - sda1 to sda5.  How would I backup the MBR (or partition table?) so that if I hose my machine with gparted (I plan on changing some partitions) I can restore my computer.  You mentioned dd but it looks like I'd have to specify a specific partition, not the whole drive?

Ideally I would love if there was an app out there that could make a bit-by-bit restore of my entire HD, partitions and all.

---

### Post by IgnorantGuru on 2008-02-01
> I have a drive with 5 partitions - sda1 to sda5.  How would I backup the MBR (or partition table?) so that if I hose my machine with gparted (I plan on changing some partitions) I can restore my computer.  You mentioned dd but it looks like I'd have to specify a specific partition, not the whole drive?

No, you only specify the drive (there is only one MBR per drive).  

To backup the entire MBR (partition table and boot code) use:
```
dd if=/dev/sda of=MBR-backup bs=512 count=1
```
(That saves it to the file named "MBR-backup" in that example)

To restore the entire MBR:
```
dd if=MBR-backup of=/dev/sda bs=512 count=1
```

To backup the boot code portion of the MBR only (excluding the partition table):
```
dd if=/dev/sda of=MBR-bootcode-backup bs=448 count=1
```

To restore boot code only:
```
dd if=MBR-bootcode-backup of=/dev/sda bs=448 count=1
```

I generally create both the MBR and the MBR-bootcode backups - they take virtually no space so it's good to have them.  Just remember that anytime you change your partition table you need to make a new MBR backup.

> Ideally I would love if there was an app out there that could make a bit-by-bit restore of my entire HD, partitions and all.

AFAIK you can use dd to do this (just omit the bs= and count= so it copies the entire "file" /dev/sda?), but the data will not be compressed as it will with partimage.  If you backup the MBR using dd and each partition using partimage, it effectively does what you want.

---

### Post by IgnorantGuru on 2008-05-27
I have just posted a Wikibooks guide "How To Backup Operating Systems" which covers this topic in greater detail...
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

Comments and suggestions are welcome.  I would also appreciate feedback on whether the guide successfully applies to Windows Vista, because I (thankfully) have no experience with that OS.  AFAIK, its methods should apply.

---

