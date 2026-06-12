---
title: "Hard Drive Issues after Hardy Upgrades"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by Malibyte on 2008-05-11
I have just upgraded (?) three machines from either Dapper LTS (2 boxes) or Gutsy (one machine) to Hardy.  All worked fine before the upgrade but I wanted to get them all on the same version; Hardy, being LTS, appeared to be the ideal way to go...however:

In all three cases, the new libata scheme for mapping hard drives (and removable devices) has b0rked things all up.  

All of the boxes have both SATA and IDE hard drives (one or two of the IDE drives are in removable bays attached to the IDE controller on the motherboard); some have other removable devices (external USB drives or internal USB card readers).

In all cases I need the first SATA drive to ALWAYS be /dev/sda (because I can't have removable devices, which may or may not be installed at any given boot, mapped ahead of the boot HD).  

For some reason, Ubuntu ALWAYS seems to map the IDE drives (or removable devices such as USB card readers) ahead of SATA drives.

How do I make sure that my boot SATA HD is ALWAYS /dev/sda?

One of the machines dual-boots with Mandriva 2008.0, running their stock kernel 2.6.22.9, which doesn't seem to have any problems mounting all of the devices (including a RAID array of three SATA drives) correctly: boot SATA drive on sda, the RAID array at sdb -> sdd, and the IDE disk on hda).  Under Ubuntu Hardy, the non-bootable IDE drive is set to sda, an old IDE LS-120 drive set to sdb, the boot SATA drive to sdc, and the RAID array at sdd -> sdf.  This machine previously ran Gutsy and did not have this problem.

Another machine boots fine without the removable IDE drive in, but if I install it the box won't boot at all because the kernel swaps the drives after it launches from grub, so it loses its root partition before it can finish booting.

I have a fourth machine that I was going to install on but am holding off for now.  When booting the live Hardy CD, I found that it installs the four slots on a USB card reader (none have cards in them) as /dev/sda, sdb, sdc and sdd; a USB floppy at sde, and the two REAL SCSI drives (on an Adaptec controller) as sdf and sdg.  This is ridiculous; the hard drives should be mapped first.

I've wasted a whole afternoon and evening screwing around with this...any tips would be helpful.

Thanks in advance...Bob

---

### Post by Rocket2DMn on 2008-05-11
Why is it so necessary that your SATA drives be mapped to sda?  If you are fstabbing, you can specify UUIDs for mount points rather than /dev locations.

---

### Post by Malibyte on 2008-05-11
> **Rocket2DMn said:**
> Why is it so necessary that your SATA drives be mapped to sda?  If you are fstabbing, you can specify UUIDs for mount points rather than /dev locations.

/etc/fstab is NOT the problem.  

The boxes WON'T BOOT because the device maps change after the kernel begins to boot up out of grub - the root partition is suddenly on a different drive than it was when the kernel launched initially from the boot loader.

---

### Post by Rocket2DMn on 2008-05-11
OK, I see what you are saying.  That is rather strange, but a search has revealed 2 relevant links that might interest you.  One is a bug report, the other is a piece of information:
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497)
[https://blueprints.launchpad.net/ubuntu/+spec/libata-for-all-ata-disks](https://blueprints.launchpad.net/ubuntu/+spec/libata-for-all-ata-disks) (for Feisty)
It seems to suggest that using UUIDs in fstab may solve the problem when it switched between GRUB and the root filesystem.  If you want me to have a look at fstab, you can post it here (may be needed from a LiveCD).
```
cat /etc/fstab
sudo fdisk -l
sudo blkid
```
If you are on a LiveCD, you will have to mount the root filesystem and post
```
cat /path/to/mount/point/etc/fstab
```

---

### Post by Malibyte on 2008-05-11
Hi -
Thanks for the links.  The bug report does seem to sum up the issue, at least for SATA and PATA drives...but - it's three years old, and the other link is pre-Feisty.  All three of these boxes worked fine before (two on Dapper and one on Feisty, then Gutsy).  The problem I'm having seems Hardy-specific.  I'd also like to know why it maps removable devices ahead of hard drives.

Anyway, here's /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1bf935ad-68dd-42ff-9e48-b04ede0c8e79 /               ext3    defaults,errors=remount-ro,data=writeback,noatime 0       1
# /dev/sda9
UUID=b36dbda1-5a53-4c0a-9744-b35881ef2d6f /home           ext3    defaults,data=writeback,noatime        0       2
# /dev/sda10
UUID=2b2ab58f-a0cd-43b3-b75d-26cc5d77aef6 /local          ext3    defaults,data=writeback,noatime        0       2
# /dev/sda5
UUID=50ff3e5b-823e-4049-85c3-99aee2da9896 /mdv            ext3    defaults,data=writeback,noatime        0       2
# /dev/sda8
UUID=c2f0e2f7-0286-4893-a3b1-9ed2a26bacec /mdvhome        ext3    defaults,data=writeback,noatime        0       2
# /dev/sda1
UUID=3304e519-a6d2-4b75-bd1d-9c342d4111ac /boot           ext3    defaults,data=writeback,noatime        0       2
# /dev/sda11
UUID=45B4-0AB7  /media/sda11    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=75F0F7A022F1C9E6 /win-sata       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=DAF4EDD1F4EDB045 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda13
UUID=995fbce6-a66e-4fc6-9c81-0ef98c6ddc67 /option         ext3    defaults,data=writeback,noatime        0       2
# /dev/hda5
UUID=45B4-0B28  /win-d          vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sde1       /msdos          msdos   defaults,umask=007,gid=46 0       1
/dev/sde2       /windoze        ntfs    defaults,umask=007,gid=46 0       1
/dev/sde6       /misc           ext3    defaults        0       1
# /dev/sda7
UUID=49471d80-57fb-4f35-8344-3b21d46ba161 none            swap    sw 0       0
/dev/md0        /raid           ext3    user,rw,exec,noauto,sync,data=writeback,noatime 0       0
/dev/sr0        /dvd            udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /floppy         msdos    rw,dev,user,noauto,exec,gid=6,umask=002 0       0
/dev/sdf        /ls120          msdos    rw,dev,user,noauto,exec,gid=6,umask=002 0       0
vader:/audio /tunes nfs rw,exec,dev,user,auto 0 0
vader:/video /video nfs rw,exec,dev,user,auto 0 0

```

Interestingly, the first time, it mapped the removable IDE HD to /dev/sde, which was OK, since it didn't affect the boot drive - and the machine booted up OK.  Now, the mapping is completely different - the IDE drive is now on sda.  UUIDs or not, it can't find the root partition (6th partition on first SATA drive) at boot.

Here's /boot/grub/device.map:
```

(fd0) /dev/fd0
(fd1) /dev/hdd
(hd0) /dev/sda
(hd1) /dev/hda
(hd2) /dev/sdb
(hd3) /dev/sdc
(hd4) /dev/sdd

```

Thanks
Bob

---

### Post by Rocket2DMn on 2008-05-11
I don't really know what to tell you.  One of the reason for using UUIDs was to help get around the problem of /dev locations changing.  Maybe this will help a bit - [http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)
If it becomes consistent at least, then you can hardcode the device.map file correctly (and do the special reinstall of GRUB it mentions).
You seem to have a pretty complex setup.  UUIDs might help for the disks you have in fstab, and maybe adding all of them to fstab would prove helpful as well (I don't see sdb, sdc, or sdd), but I don't know much about configuring RAID either, other than the basics.

If you can nail down the source of the problem (libata? grub? both?), then you may want to file a new bug report.  If you do, please post a link.
I will check up on you in the morning, good luck.

---

### Post by Malibyte on 2008-05-11
Thanks very much for your help.  I was able to get this box to boot by putting the UUIDs in the /boot/grub/menu.lst file.  It then got to the point where changing some of the non-Linux partition designators in fstab allowed the box to fully boot.  

Interestingly, the upgrade routine did not fix this; under Gutsy my old menu.lst, with this line, worked fine:

```

 kernel /vmlinuz-2.6.22-14-generic root=/dev/sda5 ro vga=0x31a

```

If the line had been changed to this during the upgrade:

```

kernel /vmlinuz-2.6.24-16-generic root=UUID=1bf935ad-68dd-42ff-9e48-b04ede0c8e79 ro vga=0x31a

```

then I probably wouldn't have torn out as much hair.  I assume that this will probably solve the problem with the other machine as well.  However, I still don't see the logic of mapping removable media ahead of hard drives, but that's not as much of an issue.  Despite the fact that the RAID drive designators have changed, it still sets up the array (/dev/md0) correctly.

Thanks again for the links and the help.

Take care
Bob

---

### Post by shadowfirebird on 2008-05-11
I'm having the same problem and I don't have any SATA drives, just IDE drives.  This is definitely a Hardy issue, at least as I experience it, because I've just upgraded from Gutsy and it worked fine there.

What I have is a hard disk with a whole bunch of different partitions on it.  All of them mount fine except two swap partitions and the "last" partition.  (Let's ignore the swap for now because it's complicated.)

The basic problem seems to be that the block device for the partition is missing (!)

Here's my /etc/fstab.  Note that we're mounting by label here.  The problem child is /dev/sda16:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=87736db3-0905-4da3-87b1-919cf3c7215e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=af6bca5e-e373-412e-b6ca-6ffce1c5d312 /boot           ext3    defaults        0       2
# /dev/hda13
UUID=74a3df22-b254-11d8-8363-9fb5a038b51d /filing         ext3    defaults        0       2
# /dev/hda10
UUID=6be1ffd6-b254-11d8-9d36-95f4129d8037 /home           ext3    defaults        0       2
# /dev/hda15
UUID=0ee9877d-1488-4500-a5f5-9c148b222d16 /mp3            ext3    defaults        0       2
# /dev/hda9
UUID=68a746c8-b254-11d8-83c4-c38043d6df30 /scratch        ext2    defaults        0       2
# /dev/hdb1
UUID=1cdc184b-3117-46cd-8543-57fda9d8866c /scratch2       ext2    defaults        0       2
# /dev/hda16
UUID=8b5bac2c-b254-11d8-9e5f-ff91cce09908 /staging        ext2    defaults        0       2
# /dev/hda6
UUID=562cf4b1-819b-4415-8e25-0044576b7793 /tmp            ext2    defaults        0       2
# /dev/hda11
UUID=d7ae9732-9916-418e-8220-3aa1dcbbba06 /usr            ext3    defaults        0       2
# /dev/hda8
UUID=9969a897-5ed5-4971-843c-89a76effe9bc /var            ext3    defaults        0       2
#
# swap on hda7 & hda14 are being handled in /etc/cryptmount/cmtab
#
/dev/hdc   /media/dvd      udf,iso9660 user,noauto,exec     0  0
/dev/hdc   /media/cdrom0   udf,iso9660 user,noauto,exec     0  0
/dev/hdd   /media/cdrom1   udf,iso9660 user,noauto,exec     0  0
/dev/fd0   /media/floppy0  auto        rw,user,noauto,exec  0  0
/dev/sde1  /media/usb1     vfat        user,noauto          0  0
/dev/sde1  /media/backup   ext2        user,noauto          0  0
/dev/sdd1  /media/ms       vfat        user,noauto          0  0
/dev/sda1  /media/sd       vfat        user,noauto          0  0

```

Here's an fdisk -l:
```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x0005f61e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2080     1048288+  83  Linux
/dev/sda2            2081      238216   119012513    5  Extended
/dev/sda5            2081        2181       50872+  83  Linux
/dev/sda6            2182        4261     1048288+  83  Linux
/dev/sda7            4262        5301      524128+  82  Linux swap / Solaris
/dev/sda8            5302       26106    10485688+  83  Linux
/dev/sda9           26107       46911    10485688+  83  Linux
/dev/sda10          46912       67716    10485688+  83  Linux
/dev/sda11          67717       88521    10485688+  83  Linux
/dev/sda12          88522       90601     1048288+  83  Linux
/dev/sda13          90602      151553    30719776+  83  Linux
/dev/sda14         151554      152593      524128+  82  Linux swap / Solaris
/dev/sda15         152594      213545    30719776+  83  Linux
/dev/sda16         213546      238216    12434152+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe29fe29f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

```

Now, watch carefully.  Nothing up my sleeves.  bklid:
```
/dev/sda1: UUID="87736db3-0905-4da3-87b1-919cf3c7215e" TYPE="ext3" 
/dev/sda5: UUID="af6bca5e-e373-412e-b6ca-6ffce1c5d312" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="562cf4b1-819b-4415-8e25-0044576b7793" TYPE="ext2" 
/dev/sda8: UUID="9969a897-5ed5-4971-843c-89a76effe9bc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="68a746c8-b254-11d8-83c4-c38043d6df30" TYPE="ext2" 
/dev/sda10: UUID="6be1ffd6-b254-11d8-9d36-95f4129d8037" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: UUID="d7ae9732-9916-418e-8220-3aa1dcbbba06" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: UUID="74a3df22-b254-11d8-8363-9fb5a038b51d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda15: UUID="0ee9877d-1488-4500-a5f5-9c148b222d16" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="1cdc184b-3117-46cd-8543-57fda9d8866c" TYPE="ext2" 
/dev/sda7: TYPE="swap" UUID="94594c65-08ea-4e56-a0a2-bb80d52f8411" 
/dev/sda14: TYPE="swap" UUID="ce69f3d7-0c70-4b43-96d3-79b8884efb6b" 

```

Oooooh!  /dev/sda16 isn't there!   It's not there if you ls /dev, either.

Any suggestions would be greatfully received...

---

### Post by Malibyte on 2008-05-11
I somehow remember having problems with having more than 15 partitions per drive...this was quite a while ago, back in the old RedHat 7 days.  But since then I've always put no more than 15 on each drive.  Interesting that you didn't have problems with it under Gutsy.

---

### Post by shadowfirebird on 2008-05-12
Yah.  I've woken up this morning and realised that my problems are all caused by the move from hda* to sda*.  

The reason that /dev/sda16 doesn't get a device file is that you can only have 15 scsi devices in a chain.  I wouldn't mind, if they actually were scsi devices...

Unless someone knows how to do an end-run around this, I guess I'm going to have to rethink my partitions.

---

### Post by Malibyte on 2008-06-17
Well, I'm still not convinced that this new way of dealing with drives does anything but suck.  

I think I'm going to have to set up udev rules just so my hard drives don't get scrambled every time I plug a USB device into my machine.  I plugged my cell phone into its USB charger tonight, then booted the machine.  Ubuntu saw the phone's memory card as a hard drive....drive order got tweaked and I got dumped out to the "Hit Control-D to continue" prompt; I did, and it then couldn't find my /home partition.  Pulled the phone off, rebooted, and all's well again.  

I have issues with VMware, too - one of my VMs uses a physical drive rather than a virtual one.  SO, of course, when /dev/sde is now /dev/sdf, things don't work right and I have to re-configure the VM so it will see the hard drive...each time there's a different number of removable devices plugged in.

** Does anyone have a better way of dealing with this than with udev rules??? **

Using UUIDs works OK (most of the time?) for locating partitions in /etc/fstab, but anything requiring a link to an actual device node will puke if anything changes.  It would be OK if the OS picked the NEXT available "drive letter" for removable devices (hey, even DOS could do that!) rather than the FIRST, or one in the middle of the chain.

Thanks
Bob

---

### Post by Rocket2DMn on 2008-06-17
You can set labels on different devices so they always mount at the same place when automounted with HAL (assuming the labels are unique).  This is the best I can do for you at the moment - [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
The /dev locations will still change depending on the order you plug in, though.
Not sure what the deal will be when you plug in new devices though.

---

### Post by Marlo_nl on 2008-07-08
Malibyte, shadowfirebird,

I'm not sure if the root cause for your problems is the same as for me, but what we do have in common is that we use a "large" number of partitions on our hard drives.

Large for Hardy that is. For Feisty and Gutsy I had no problems with my HDD partitioning.

Maybe you can have a look at:

[http://ubuntuforums.org/showthread.php?t=852407](http://ubuntuforums.org/showthread.php?t=852407)


Please let me know if you recognize the behavior described in that thread.

Regards, Marlo

---

### Post by Malibyte on 2008-07-10
Mario -

I have been in the habit of not using more than 15 partitions on ANY hard drive for years; maybe I never broke my old SCSI habits.  So, in my case, that's not the problem.

Thanks
Bob

---

### Post by |Eric| on 2008-07-10
why do /dev location moves ? ubuntu is the first linux system i encounter with this "issue"
tho its the first Sata booted linux i install i never had any of such a problem on any other linux 

can sombody care to elaborate ?

thanks for the info btw about the UUID command didnt know that one 

in fact its the firstime  i see a fstab with UUIDs ... 
on windows ok i seen uuid but for somthing else ....

---

### Post by Rocket2DMn on 2008-07-10
> **|Eric| said:**
> why do /dev location moves ? ubuntu is the first linux system i encounter with this "issue"
tho its the first Sata booted linux i install i never had any of such a problem on any other linux 

can sombody care to elaborate ?

thanks for the info btw about the UUID command didnt know that one 

in fact its the firstime  i see a fstab with UUIDs ... 
on windows ok i seen uuid but for somthing else ....

/dev locations can move if the drives are detected in a different order between boots.  This can be caused by race conditions, or hardware just acting irregularly (like maybe sometimes one drive is slower to spin up than the other).  Since there isn't anything we can do about that, UUIDs come in to play.

---

### Post by Marlo_nl on 2008-07-14
> **Malibyte said:**
> 

I have been in the habit of not using more than 15 partitions on ANY hard drive for years; maybe I never broke my old SCSI habits.  So, in my case, that's not the problem.

Thanks
Bob


Bob, thanks for letting me know.


I'm afraid that my "too many partitions" problem is rather "unique". 
Unfortunately I've not yet found a post on this forum with a similar problem description or even better a solution for the problem. 
So for the time being I'm forced to stick with Ubuntu 7.10.


Regards, Marlo

---

### Post by Malibyte on 2008-07-14
The UUID fix has solved the problem of booting and mounting partitions, but there are certain things it can't deal with.  I assume that such issues were not on the devs' radar when this new "feature" was implemented.  

In my case, the biggest problem is VMware.  One of my VMs uses a couple of **physical** partitions on an IDE drive (I have to be able to dual boot the box sometimes due to VMware's limitations with USB connectivity (PDAs, iPods, etc.)).  I don't want to make this a virtual drive. 

Well...sometimes that hard disk comes up as /dev/sda, sometimes as /dev/sde.  When it decides to change device designators, I need to physically change the VM's parameters (delete, then add back the hard drive) and restart it...a royal pain in the @$$.  If someone has a fix for this, I'd appreciate a pointer to it - thanks!

Thanks
Bob

---

### Post by Malibyte on 2008-07-31
Hi all -

I need to come up with a udev rule to make sure that two of my hard drives always come up on the same /dev/sdX nodes.  The current randomness is making it very difficult for me to use VMware with VMs on a physical drive.  It appears that these are set in /etc/udev/60-persistent-storage.rules.  However, the comments in that file say not to edit it, as it gets overwritten.

Anyone have a rule they're willing to share, and where to put it?

Thanks
Bob

---

### Post by Rocket2DMn on 2008-07-31
I see a new thread in your future...
:lolflag:

---

### Post by Malibyte on 2008-07-31
> **Rocket2DMn said:**
> I see a new thread in your future...
:lolflag:

Yeah, maybe you're right.  Flogging this dead horse any more won't help much....!

---

