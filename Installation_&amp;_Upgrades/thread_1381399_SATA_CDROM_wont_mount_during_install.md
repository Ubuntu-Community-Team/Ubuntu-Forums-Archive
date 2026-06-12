---
title: "SATA CDROM wont mount during install"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by dave_mystic on 2010-01-14
Hi, new to Ubuntu, used to do BSDI unix for 15 years or so.

I am trying to install Ubuntu 8.04LTS Server on a Dell PowerEdge T105 with SATA CD/DVD and add-in SAS6iR controller for RAID.

Downloaded ubuntu-8.04.3-server-amd64.iso and have burned several CDROMS, including one at the lowest speed.

When I boot the install CDROM, I receive an error after the keyboard stuff when it trys to mount the CDROM.

I have switched to the console, and tried various mount commands, including:
# mount -t iso9660 -r ro /dev/scd0 /cdrom

to which I receive the message 
mount: Mounting /dev/scd0 on /cdrom failed: Invalid argument.

I belive I have the correct device as I can issue the same commend without a CD in the drive, and I get the message 
mount: Mounting /dev/scd0 on /cdrom failed: No medium found.

I've poked around with modprobe, and searched this forum, but so far I don't have any answers.

Here's hoping that someone can help me determine where to look to find the problem/solution.

TIA!!

---

### Post by Dscottmc7 on 2010-01-16
Dave, possibly similar thread so I'm posting it just with the hope of "HELP!"
In 9.04 an upgrade killed off my CDROM and after legion attempts to fix I gave up...no more time...(but could still detect and mount ONLY the Ubuntu boot disk)...

Clean install of 9.10 in December.  Bingo!  detected the CDROM as optical Drive!  Read old Windows CD of 6 years ago!  In the euphoria of the moment I went to "eject" and with a nostalgic tear fogging my eyes I hit "UNMOUNT" instead of "EJECT"   ...BAMB!!!  CDROM no longer...

mount command does not work
/etc/fstab/ is screwy and I don't know how to get it cleaned up in the boot scripts (as if I knew BOOT SCRIPTS!)
The line in fstab was: /dev/scd0 /media/cdrom0  udf,iso9660 user,noauto,exec,utf8     0  0 

All the major dvd files are under /usr/bin/
/dev/media/ has both cdrom and cdrom0 (which both folders are empty)

/dev/ has the block file (sr0) and "Block" folder,
/dev/block/11.0 (references cdrom) which links to "block device"

CDROM Optical Drive is on IDE Host controller SCSI 0.0.1.0. but "device not detected."

Obviously I'M WAY IN OVER MY HEAD AND SCREWED UP!  does anyone have the patience to help me out of this mess?

Here's the common thread for 10 months:  CDROM not detected upon upgrade.
Thanks...

---

### Post by wlraider70 on 2010-01-17
@Dscottmc7 did you reboot.
Un mount is not a big deal, it should remount. 

try this

 Re: Unable to mount cdrom0
ok if you can see your cdrom lets try to forcebly mount it via terminal:
```


sudo mkdir /media/cdrom-test


```

```


sudo mount /dev/scd0 /media/cdrom-test


```

put some cd in drive and then run below:
```


ls -al /media/cdrom-test


```

---

### Post by Dscottmc7 on 2010-01-17
Thanks, Luke...
tried, but no luck.
Thanks for the direction...I made a symbolic link between files such that in the end a printout would be:
/dev$ ls -al /media/cdrom-test:
total 8
drwxr-xr-x 2 root root 4096 (date...)
drwxr-xr-x 20 root root 4096 (date...)
drwxrwxrwx 1 root root 10 (date...) cdrom -> dev/cdrom
drwxrwxrwx 1 root root 10 (date...) cdrw -> devcdrw
drwxrwxrwx 1 root root 10 (date...) dvd -> /dev/dvd
drwxrwxrwx 1 root root 10 (date...) dvdrw -> /dev/dvdrw
drwxrwxrwx 1 root root 10 (date...) sr0 -> /dev/sr0

BUT still no cigar.  The CDROM hardware is not detected, but I can find it only in the computer chain attached and named on the SCSI with the BUS ID of pci-0000:00:1f.2-scsi-0:0:1:0.

It seems I've tried every obvious, logical approach except 2:  the right one or one that can attach hardware by bus ID, (even "discover" doesn't id it!)

Thanks, buddy...I'll keep trying.  Got a major presentation coming up next weekend...maybe I'll have to cave in and truck off to Staples!
:(

---

### Post by falconindy on 2010-01-17
> **dave_mystic said:**
> Hi, new to Ubuntu, used to do BSDI unix for 15 years or so.

I am trying to install Ubuntu 8.04LTS Server on a Dell PowerEdge T105 with SATA CD/DVD and add-in SAS6iR controller for RAID.

Downloaded ubuntu-8.04.3-server-amd64.iso and have burned several CDROMS, including one at the lowest speed.

When I boot the install CDROM, I receive an error after the keyboard stuff when it trys to mount the CDROM.

I have switched to the console, and tried various mount commands, including:
# mount -t iso9660 **-r ro** /dev/scd0 /cdrom

Your mount command is wrong. -r is to specify read only, ro is an optarg to -o. Together, they make no sense ('-r' or '-o ro' would), and alone they're superfluous as a CD will never be mounted anything BUT read-only.

That said, if a device node is being created (and it is as far as I can tell), then your device is being recognized. You can probably probe it for more info as follows:

udevadm info -q all -n /dev/cdrom

---

### Post by andydread on 2010-01-23
I am also having the same exact problem with UBUNTU Server 8.04.3 AMD64 and Dell Poweredge server T105.  I booted another PC with the same CD-ROM and the CD-ROM works fine.  So its only happening on this Dell server T105. I boot the i386 version and it finds the CD-ROM ok so this only happens with the AMD64 version of Ubuntu Server 8.04.3. and not the i386 version of 8.04   

Right after keyboard selection it looks for the CD-ROM then i get this. 

```
Your installation CD-ROM couldn't be mounted.  This probably means that the CD-ROM was not in the drive.  IF so you can insert it and try again
```

Ok The solution for this problem is found in this thread. [http://ubuntuforums.org/showthread.php?t=768833](http://ubuntuforums.org/showthread.php?t=768833)
Basically press F6 then add mem=4G to the end of the kernel install line in the install boot menu

---

### Post by dave_mystic on 2010-03-19
> **andydread said:**
> Ok The solution for this problem is found in this thread. [http://ubuntuforums.org/showthread.php?t=768833](http://ubuntuforums.org/showthread.php?t=768833)
Basically press F6 then add mem=4G to the end of the kernel install line in the install boot menu

Egg Salad!! :P (or 'Excellent!' for those who are want strict pronunciations.)

Finally returned to this project after a lot of traveling and checked the forum to see what might have been posted.  Followed the instructions above as indicated.  Couldn't be easier, and it just worked.

Thank you andydread, you found a post that I didn't see.

---

