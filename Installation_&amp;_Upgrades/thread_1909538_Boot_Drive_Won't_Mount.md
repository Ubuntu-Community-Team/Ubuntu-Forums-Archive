---
title: "Boot Drive Won't Mount"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by cscomp3 on 2012-01-15
Recently, upon boot, we saw a BIOS message that something was wrong with  the hard drive.  Then when Ubuntu attempted to load from the hard disk,  we recd this message:

------------------------
mount: mounting /dev/disk/by-uuid/cc8a9ae1-66cf-45d8-9d7b-f470f3169342 on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
------------------------

In trying to fix it, I found this thread:

[http://ubuntuforums.org/showthread.php?t=1788381](http://ubuntuforums.org/showthread.php?t=1788381)

After reading it, I made a LiveCD from Ubuntu with 10.04 LTS.  Then when it booted from CD, I ran the following command in the terminal (as recommended in the above thread):

e2fsck -f -y -v /dev/sda1

Did not help.  Then I checked the hard drive through the booted Ubuntu  and found it was listed as /dev/sda, so I ran this command in the terminal:

e2fsck -f -y -v /dev/sda

Nothin'.

I can see the drive from the LiveCD as /dev/sda, but Ubuntu says there is no data on the disk.  It's as if there is no "FAT" present or the Linux equivalent file table.

Help!  We have a lot of pics stored in the machine and, as usual,  have not backup up in a while.  I think the disk is retrievable and  repairable, I just don't know how yet.

Assistance is much appreciated to get this disk back working.

And what is "BusyBox"?

Thank you.

cscomp3

---

### Post by darkod on 2012-01-15
Is the hard disk recognized correctly in BIOS?

Seems like the partition table is corrupted or gone. You can try scanning for errors with fixparts:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Or scanning the disk and recovering partitions with testdisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

What ever you do, DO NOT write a new blank partitions table if it ever asks you. And DO NOT install another ubuntu over the existing one (or next to it) thinking it might help read the data. It can destroy a large part of it.

---

### Post by cscomp3 on 2012-01-15
Thanks.

Yes.  The hard disk is recognized in BIOS.

I like what TestDisk has to say in the write-up, esp about locating the backup SuperBlock and copying files from deleted ext3 partitions.

I will try to run it with my LiveCD.

Thanks, again.

cscomp3

---

### Post by cscomp3 on 2012-01-21
Got TestDisk to run under the 10.04 LiveCD using a thumb drive.

TestDisk does not even see the drive at all, even though Ubuntu Disk Utility sees the drive.  However, Ubuntu Disk Utility says the drive is not partitioned.

---

### Post by darkod on 2012-01-21
Hmmm, doesn't sound good. Usually testdisk is very good in at least seeing the disk is there, even if it can't recover the partitions.

But if it doesn't see it at all, something really bad might have happened to it.

I have no idea, if the disk is not seen at all or not seen correctly, there is not much software you can use to recover the files/partitions.

---

### Post by sudodus on 2012-01-21
Try also ***gpart*** (you get it from the internet). If that fails, it is always possible to use ***PhotoRec***.

Even without a partition table and file system, a lot of the file data is still there on the hard disk drive. PhotoRec works by identifying the headers of the files and can identify many common file types. It was originally made to recover photo files from flash cards, but today it can recover many other file types including documents and videos. But it is not convenient, because the file names and directory structure is not restored by PhotoRec.

---

### Post by cscomp3 on 2012-01-21
I tried FixParts.  It can't read the master boot record.  I tried to backup the partition table with sfdisk, but sector 0 could not be read.

I just tried PhotoRec, but it did not see /dev/sda either.

Going to try gpart . . .

Thanks for your post and suggestions, otherwise known as help.

---

### Post by sudodus on 2012-01-21
There may be different iso images with PhotoRec. Did you download this one
[[COLOR="red"]_http://www.sysresccd.org/System-tools_[/COLOR]]("http://www.sysresccd.org/System-tools") or this one
[[COLOR="Red"]_http://ubuntu-rescue-remix.org/Download_[/COLOR]]("http://ubuntu-rescue-remix.org/Download")

Since Ubuntu can see the drive, maybe another rescue-tool can also see it, and then PhotoRec has a chance to do its task. Chances are fairly good that at least one version of ***ubuntu-rescue-remix*** can see the drive.

---

### Post by cscomp3 on 2012-01-21
I have an ext3 partitioned drive.  gpart says it only works with ext2.

Trying one more thing for the day . . . the "e2fsck -f -y -v /dev/sda" command again.

---

### Post by cscomp3 on 2012-01-21
Thanks.  I'll try those too.

I used the photorec that came with testdisk.

---

### Post by cscomp3 on 2012-01-21
Well, I tried PhotoRec on the remix CD.  It won't see the hard drive either.  Neither will TestDisk on the remix CD.  I ran boot_info_script after booting with the Ubuntu 10.04 LiveCD and the system does not even think /dev/sda is a hard drive.  Here is the results file:

 ```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================


============================ Drive/Partition Info: =============================

no valid partition table found
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sda 

=============================== StdErr Messages: ===============================

ERROR: asr: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sda" to 4608
ERROR: hpt45x: seeking device "/dev/sda" to 18446744073709545984
ERROR: isw: seeking device "/dev/sda" to 18446744073709550592
ERROR: isw: seeking device "/dev/sda" to 18446744073709551104
ERROR: isw: seeking device "/dev/sda" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sda" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sda" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sda" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sda" to 137438913024
ERROR: pdc: seeking device "/dev/sda" to 137438920192
ERROR: pdc: seeking device "/dev/sda" to 137438927360
ERROR: pdc: seeking device "/dev/sda" to 137438934528
ERROR: sil: seeking device "/dev/sda" to 18446744073709551104
ERROR: via: seeking device "/dev/sda" to 18446744073709551104
ERROR: asr: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sda" to 4608
ERROR: hpt45x: seeking device "/dev/sda" to 18446744073709545984
ERROR: isw: seeking device "/dev/sda" to 18446744073709550592
ERROR: isw: seeking device "/dev/sda" to 18446744073709551104
ERROR: isw: seeking device "/dev/sda" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sda" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sda" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sda" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sda" to 137438913024
ERROR: pdc: seeking device "/dev/sda" to 137438920192
ERROR: pdc: seeking device "/dev/sda" to 137438927360
ERROR: pdc: seeking device "/dev/sda" to 137438934528
ERROR: sil: seeking device "/dev/sda" to 18446744073709551104
ERROR: via: seeking device "/dev/sda" to 18446744073709551104

```If anyone has any other ideas, let me know.

Thanks as always.

cscomp3

---

### Post by sudodus on 2012-01-22
> **cscomp3 said:**
> Well, I tried PhotoRec on the remix CD.  It won't see the hard drive either.  Neither will TestDisk on the remix CD.  I ran boot_info_script after booting with the Ubuntu 10.04 LiveCD and the system does not even think /dev/sda is a hard drive ...
1. I suggest that you try the Ubuntu-Rescue-Remix ***version 10.04***, since Ubuntu 10.04 can see your drive. You find it by scrolling down the page I linked to yesterday, but directly via this link

[[COLOR="Red"]_http://ubuntu-rescue-remix.org/node/466_[/COLOR]]("http://ubuntu-rescue-remix.org/node/466")

2. If Ubuntu-Rescue-Remix 10.04 does not work I suggest that you try to clone your drive to an empty hard disk drive of at least the same size, and do the recovering from that drive instead.

a. As long as the Ubuntu install CD or USB drive can see it, you should be able to use dd. It is a very powerful too, but therefore also very risky. It is nick-named 'disk destroyer', because when people apply it the wrong way, it does not ask, but overwrites your data. To clone from drive /dev/sda to drive /dev/sdb, run the following command
```
sudo dd if=/dev/sda of=/dev/sdb bs=4096 & pid=$!
``` It takes ***several*** hours, and prints no output, so don't despair. If you get curious, you can push it to write some lines by sending the following kill command (yes kill).
```
sudo kill -USR1 $pid
```

b. Try some other cloning tool hoping that it's underlying operating system can see your hard disk drive. One alternative is Clonezilla.

c. If the problem is that some part of the drive is physically damaged, ***ddrescue*** would be the best alternative, but even if the drive hardware is good, ddrescue is a good alternative to standard dd. But it is also very powerful and risky. I think it is included in Ubuntu-Rescue-Remix, and it can easily be installed into the live session of Ubuntu 10.04 by
```
sudo apt-get install ddrescue
``` The info pages are well written, so after installation, please read
```
info ddrescue
```

---

### Post by cscomp3 on 2012-01-22
Wow.  Thanks for the detailed reply.  You obviously put some time into that.

A couple of quick clarifying questions:

- I know the drive is an ext3 drive.  Is the "dd" command line you provided set for ext3?

- One of the programs I tried stated it could not find or read the Master Boot Record and had an option to write a MBR to the disk.  It may have been TestDisk from the remix CD.  Since Ubuntu sees "a device" at /dev/sda but not as a hard drive, could I write the MBR to the disk and then use "e2fsck" to try and get the backup Superblock and re-write it to the correct location on the drive?  Or by writing a new MBR, will I simply be ending the process of data recovery.  The thing that has never happened in this process is Ubuntu, or any other program, seeing the device as an actual hard drive.

And I do have the 10.04 remix CD.  I have tried to stick with 10.04 through this whole process.  Your post let me know I did the right thing.

This is certainly a pain, but I am also learning a lot.  That is good.  Very good.  The great thing about Linux is the community of folks willing to share their knowledge.

Thanks, again.

cscomp3

---

### Post by sudodus on 2012-01-22
> **cscomp3 said:**
> ...
- I know the drive is an ext3 drive.  Is the "dd" command line you provided set for ext3?

dd can operate on files, partitions and whole drives, so it is certainly ***no problem*** that it is an ext3 drive (or to be correct, a drive with a partition with the ext3 file system). This holds also for ddrescue.

> - One of the programs I tried stated it could not find or read the Master Boot Record and had an option to write a MBR to the disk.  It may have been TestDisk from the remix CD.  Since Ubuntu sees "a device" at /dev/sda but not as a hard drive, could I write the MBR to the disk and then use "e2fsck" to try and get the backup Superblock and re-write it to the correct location on the drive?  Or by writing a new MBR, will I simply be ending the process of data recovery.  The thing that has never happened in this process is Ubuntu, or any other program, seeing the device as an actual hard drive.
...
It should not damage the disk to write a MBR to the disk. It means writing into the first 512 bytes of the drive, and it should not write anything to the rest of the drive. Actually, this might be a big step forward, because TestDisk probably has a good reason to complain about it (that it is actually damaged).

If that works, great! Otherwise, it might be damaged physically, and it would make sense to clone the disk to another one as I suggested earlier, because after the cloning, you will be able to write a fresh MBR to that new disk. In that case, clone with ddrescue (which is very good at identifying bad sectors and cloning the good parts of damaged disk drives).

---

### Post by cscomp3 on 2012-01-22
I like it!  O.K.  A new MBR using the remix CD.  If that doesn't get me going in the right direction, cloning with ddrescue.

I'll post with results, which may be a while if I have to find a new drive.  And I have to turn a baby crib with cut-off legs into a puppy kennel sometime this week . . .

Thanks, Again!

cscomp3

---

### Post by sudodus on 2012-01-22
Good luck :-)

---

### Post by cscomp3 on 2012-01-22
Thanks.  I wrote the MBR and got an "Error 28".  Now the BIOS won't even let the PC boot.  It keeps sending me to setup.  Can't figure that one out.  When and if I can get the PC to boot, I'll try "e2fsck" to recopy the Superblock backup.

I poked around on the 'net and since I got the "Error 28", I am starting to expect internal physical damage, which, as you say above, would lead me toward cloning the drive.

Again, thanks for all your help.

I'm off to convert that baby crib!

cscomp3

---

### Post by cscomp3 on 2012-07-13
I gave up on the drive.  I figure hardware failure.  I found another drive and installed 12.04LTS.

Baby Crib converted and still working nicely.  Small dog.

Now on to the rabbit cage . . .

Thanks, All.  cscomp3

---

