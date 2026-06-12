---
title: "[SOLVED] Hangs at boot"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by nextbgates95 on 2008-02-10
Hello.  I have a strange issue that no one else seems to be having.  I have tried numerous times to install Linux Mint.  Since I knew Linux Mint was a fork of Ubuntu, and having an Ubuntu cd, I decided to try and install it.  I get the same errors when trying to boot either one.  The message I get is:

********
*drops to busybox*
ata.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 cdb 0x5a da ta 4096 in
********

and it just keeps repeating.  I have a Maxtor D740x-6L 40gb drive I would like to install on.  The thing is, when removing this drive and trying to boot, I can.  I also have a 160gb WD drive with XP on it, SCSI.  The Maxtor drive is connected to the cd drive on the same IDE cable.  

What should I do?

---

### Post by Rocket2DMn on 2008-02-10
If the drive is in the slave position on the IDE cable, make sure the jumpers are set correctly on it.  Otherwise it seems like the disk may be corrupted, possibly physically.
You can try booting from the LiveCD, opening GParted (System->Administration->Partition Editor) and formatting the 40GB drive to ext3.  If that works, you should run fsck on it.  So, let's say the drive is at /dev/hda1 you would run
```
sudo fsck /dev/hda1
```

Make sure you don't format your windows drive!  If you are unsure, post the output of
```
sudo fdisk -l
```

---

### Post by nextbgates95 on 2008-02-10
OK thanks, I will try that soon.  I am on my friend's computer.  I cannot boot into Ubuntu or Linux Mint if the drive is plugged in.  I have the hard drive set as the master and the CD Drive set as slave, with the correct jumper positions.  I was able to boot into Puppy Linux to format and partition using Gparted.  May I inquiery as to what fck does?  I have also looked at fdisk -l, and it does not list the Maxtor drive.  I do see my windows drive mounted as /dev/sda, though.

Thanks for the fast response:KS

---

### Post by Rocket2DMn on 2008-02-10
fsck is like chkdsk in windows, it scans the drive for errors.  If "sudo fdisk -l" doesn't show the drive, it's either not configured correctly in hardware (plugs or jumpers) or the drive is broken and needs to be trashed/replaced.
You need to use sudo on fdisk or it won't display all the info though.

---

### Post by nextbgates95 on 2008-02-10
OK....I am in the process of running fsck.  In Puppy Linux, I can mount and work with the Maxtor drive.  It also shows up when doing "fdisk -l"(Puppy has no "sudo" command).  Will ext2 work with Ubuntu?  I cannot fsck the drive in Puppy unless it is ext2.

---

### Post by wpshooter on 2008-02-10
> **nextbgates95 said:**
> OK thanks, I will try that soon.  I am on my friend's computer.  I cannot boot into Ubuntu or Linux Mint if the drive is plugged in.  I have the hard drive set as the master and the CD Drive set as slave, with the correct jumper positions.  I was able to boot into Puppy Linux to format and partition using Gparted.  May I inquiery as to what fck does?  I have also looked at fdisk -l, and it does not list the Maxtor drive.  I do see my windows drive mounted as /dev/sda, though.

Thanks for the fast response:KS

Assuming you have 2 IDE connectors on your motherboard, have you tried putting the 40GB hard drive on the Primary IDE connector jumpered as Master and put the CD drive on the Secondary IDE connector jumpered as Master ?  And then try making your IDE drive the first boot device in BIOS ?

---

### Post by Rocket2DMn on 2008-02-10
> **nextbgates95 said:**
> OK....I am in the process of running fsck.  In Puppy Linux, I can mount and work with the Maxtor drive.  It also shows up when doing "fdisk -l"(Puppy has no "sudo" command).  Will ext2 work with Ubuntu?  I cannot fsck the drive in Puppy unless it is ext2.

Yes, ext3 is the default filesystem which is just ext2 + journaling.

---

### Post by nextbgates95 on 2008-02-10
OK.  Here are the results:

```
Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4866    39086113+  83  Linux

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9       18845   151308202+   7  HPFS/NTFS
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ...

```

and

```
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hdb1: clean, 11/4889248 files, 153440/9771528 blocks
```

Should it work?

---

### Post by Rocket2DMn on 2008-02-10
You should be good to go with your install (on the hdb drive).  Just make sure you don't overwrite Windows!  Remember, you will need at least 2 partitions on hdb, a root (/) and a swap partition.  Optionally, you can have a separate /home partition - if you choose to do this, make it large and store your data like pictures/music/videos here.  In this case, the root partition doesn't need to be huge.  Maybe, 10-15GB for root, 1.5x-2x your RAM capacity for swap, and the rest for /home (~20-30GB).

---

### Post by nextbgates95 on 2008-02-10
Sad to say it has the same exact issue..........more help please!

---

### Post by Rocket2DMn on 2008-02-10
How much RAM do you have on this machine?  There can be problems when trying to run the LiveCD with less than 256MB of RAM.  Also, how old is this hard drive?

---

### Post by nextbgates95 on 2008-02-10
I have 1 gig of RAM; the hard drive is not that old.  It was in an old computer that had to have the drive replaced a few years back.  It was the replacement drive I removed before disposing of the computer.

---

### Post by Rocket2DMn on 2008-02-10
OK, for now we will assume the disk is still good, so do wpshooter's suggestion in post 6 and put the drive as a master on a second IDE connector if you can and try it then (make sure you set the jumpers, too).  If this fails, I would have to make the leap and say that your drive is somehow physically corrupted and should not be used (even though fsck didn't detect anything).

---

### Post by nextbgates95 on 2008-02-10
Well, I Do not have a second IDE controller on the motherboard.  If there are no more options, I would be fine with downsizing WD 160 gb Disk, but I cannot resize it through GParted.  It tells me to chkdsk the drive and then reboot twice.  Following those directions has no effect.  If you can solve that problem, I should be alright.

Thank you

---

### Post by Rocket2DMn on 2008-02-10
The disk should be defragmented in windows at least once, probably twice if it's had a fair amount of usage.  Then chkdisk it, reboot twice, then shut down windows normally (not hibernate), then you should have better luck resizing.

---

### Post by nextbgates95 on 2008-02-11
OK...I am in the process of defragmenting.  I do not think it will work very well, though, as the before and after look almost identical.  But we shall see.

---

### Post by nextbgates95 on 2008-02-11
OK!!! I was able to get it installed on the 160 gb drive.  Thank you!

---

