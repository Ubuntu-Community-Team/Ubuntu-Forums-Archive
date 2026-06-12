---
title: "Feisty Upgrade -- doesn't see hard drives"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by reuben on 2007-04-13
My system is broken after a feisty upgrade. It can't see /dev/hda5, /dev/hdb. One of  these contains my home partition, so kdm won't let me into KDE.

How can I fix?

Thanks

---

### Post by Bert Mariën on 2007-04-13
Check these files:

/etc/fstab
/etc/mtab


Use UUID to identify your partitions. 

Check in /dev/.udev/db if any UUID's have changed and correct them in the above mentioned files.

---

### Post by muncrief on 2007-04-13
Please see my mini Howto on how to update to the latest Feisty. Aptitude is broken, but the kernel hard drive problem that brought down so many systems starting yesterday has been fixed. However, if you don't upgrade correctly you probably won't get the correct kernel at this time.

 I hope this helps. Here's the link:

[http://ubuntuforums.org/showthread.php?t=408860](http://ubuntuforums.org/showthread.php?t=408860)

---

### Post by reuben on 2007-04-13
More info on this problem; it seems that something decided to rename the drives. I don't have UUIDs in my /etc/fstab; it looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7 /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6 /home           reiserfs defaults        0       2
/dev/sda1 /mm1            ext3    defaults        0       2
/dev/sda5 /tmp            ext3    defaults        0       2
/dev/hda1 none            swap    sw              0       0
/dev/hdb /mm2            ext2    defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

sda6 and sda5 used to be named hda6 and hda5, and the fstab referred to them.

sda1 and hdb are still MIA (i.e. /mm1 and /mm2). How can I track these down?

fdisk -l gives this:

Disk /dev/sda: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1052226   82  Linux swap / Solaris
/dev/sda2             132        4867    38041920    5  Extended
/dev/sda5             132         513     3068383+  83  Linux
/dev/sda6             514        3062    20474811   83  Linux
/dev/sda7   *        3063        4867    14498631   83  Linux

---

### Post by reuben on 2007-04-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/106408](https://bugs.launchpad.net/ubuntu/+bug/106408) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Anybody know how I can get mm1 and mm2 back? They contain all my music & vids ... :(

---

### Post by reuben on 2007-04-13
My cdrom drives are not being found either. :(

---

### Post by siucdude on 2007-04-14
I have a laptop that has two SATA drives and same thing, there are few bugs open on this subject but nothing,  My Edgy CD works no problem but when I try the Feisty, I get no play it can't even find them for partition.  
I feel your pain.

Here is one of the bugs open, --- [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/97367](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/97367)

---

### Post by Bert Mariën on 2007-04-14
> **reuben said:**
> More info on this problem; it seems that something decided to rename the drives. I don't have UUIDs in my /etc/fstab; it looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7 /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6 /home           reiserfs defaults        0       2
/dev/sda1 /mm1            ext3    defaults        0       2
/dev/sda5 /tmp            ext3    defaults        0       2
/dev/hda1 none            swap    sw              0       0
/dev/hdb /mm2            ext2    defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

sda6 and sda5 used to be named hda6 and hda5, and the fstab referred to them.

sda1 and hdb are still MIA (i.e. /mm1 and /mm2). How can I track these down?

fdisk -l gives this:

Disk /dev/sda: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1052226   82  Linux swap / Solaris
/dev/sda2             132        4867    38041920    5  Extended
/dev/sda5             132         513     3068383+  83  Linux
/dev/sda6             514        3062    20474811   83  Linux
/dev/sda7   *        3063        4867    14498631   83  Linux

Here I am again. Sorry, I had to go to sleep some wee hours.

Back to the topic.

You have not been reading it write, Reuben.
I wrote "use UUID", I didn't write that they would be in your files yet.

let's take it from the beginning. 

Reading your files, I assume that they are all Linux partitions. If not let me know., because you might need ntfs-3g.

Go to this directory:

/dev/.udev/db

You'll find a lot of files there. Look for the files that end with your partition name.

e.g. You have a partition sda1, so look for a file looking more or less like this:

%2block%2sfda%2fsda1

Open that file and you'll find the UUID there.
Search for all your other partitions as well.

Now open your /etc/mtab file.
Check the file to see if all your mount points are there. If not, you have to fill in the gabs yourself by hand.

Open the /etc/fstab file.
Now you have to change things.

I still use your sda1 as an example.

Change your entry for sda1 so it looks like this:

# Entry for /dev/sda1
UUID=AF9D16F6A214AAB9 /mm1            ext3    defaults        0       2

DON'T copy this UUID, that's mine. You have to replace that UUID with the one you found in /dev/.udev/db.

Do this for all your partitions.

Save all files.

Check in /media if all your mount points are there. If not: create them.

After that, reboot and everything should be back.

Good luck!

---

### Post by Bert Mariën on 2007-04-14
CORRECTION
I had a line to many in this/

Change your entry for sda1 so it looks like this:

# Entry for /dev/sda1
UUID=AF9D16F6A214AAB9 /mm1 ext3 defaults 0 2


By the way, if your drives are renamed sda instead of hda etc, When searching for the UUID look for files according to the CURRENT name of your drives and change your /etc/mtab and /etc/fstab files accordingly.

Again: GOOD LUCK!

---

### Post by Bert Mariën on 2007-04-14
> **reuben said:**
> My cdrom drives are not being found either. :(

Check if your cdrom drive names haven't been changed as well.
If so, again change those names in the /etc/fstab file. 

Then check your mount points for the cd drivesas well (if not there, create).

Reboot.

---

### Post by reuben on 2007-04-14
Good tips, but no dice so far.

The other drives/partitions are not listed in that folder either:

[email]reuben@mediabox:/dev/.udev[/email]/db$ ls | grep da
%2fblock%2fsda
%2fblock%2fsda%2fsda1
%2fblock%2fsda%2fsda2
%2fblock%2fsda%2fsda5
%2fblock%2fsda%2fsda6
%2fblock%2fsda%2fsda7

I'm going to do a fresh install from CD and see if that helps. Will post here then.

---

### Post by reuben on 2007-04-14
There must have been some conflict caused by dist-upgrade. The installer picked up the drives no problem, and as hd* rather than sd*; the new fstab has uuids. All seems good now.

---

### Post by Bert Mariën on 2007-04-14
If you're out of the woods and everything works, I suppose you are a lucky man (grin). 

Just let me know if you still encounter problems with your disks.

---

### Post by reuben on 2007-04-14
Man did I speak too soon.

It worked fine on the first boot after the install. But on the second boot it's back to the same situation. Here's my fstab, post installer:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=99e436a5-6a3f-4932-b85a-70fb263b4afd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=0aeed028-94da-11d9-88ec-bda3b4dd8f69 /home           reiserfs defaults        0       2
# /dev/sda1
UUID=e19a4234-d7e3-45a7-b369-b6c1724ba0c6 /mm1            ext3    defaults        0       2
# /dev/hdb
UUID=1e1bc211-0907-488e-a47c-4f41565c872f /mm2            ext3    defaults        0       2
# /dev/hda5
UUID=c7d10a87-3e04-4fbe-83ef-7e0a5541eb64 /tmp            ext3    defaults        0       2
# /dev/hda1
UUID=b41e32a6-4367-47ab-8885-01974ca0fb27 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0


fdisk -l is identical to earlier.


There was some message during checkfs at boot that complained about the two special devices not being found, but I can't find that in any of the logs.

---

### Post by reuben on 2007-04-14
Here's the checkfs log. Again, these worked fine on the first reboot after install, but haven't subsequently. They ARE detected by the BIOS.


fsck 1.40-WIP (14-Nov-2006)
Replaying journal..
Reiserfs journal '/dev/sda6' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Reiserfs super block in block 16 on 0x806 of format 3.6 with standard journal
Blocks (total/free): 5118688/2807430 by 4096 bytes
Filesystem is clean
fsck.ext3: Unable to resolve 'UUID=e19a4234-d7e3-45a7-b369-b6c1724ba0c6'
fsck.ext3: Unable to resolve 'UUID=1e1bc211-0907-488e-a47c-4f41565c872f'
/dev/sda5: clean, 14/384000 files, 29593/767095 blocks
Reiserfs super block in block 16 on 0x806 of format 3.6 with standard journal
Blocks (total/free): 5118688/2807430 by 4096 bytes
Filesystem is clean
fsck died with exit status 8

---

### Post by Bert Mariën on 2007-04-14
So, what you do know:

1. Check the UUID again as you did before. (/dev/.udev/db) If changed, modify your fstab and mtab files accordingly.

2. Your mm1 and mm2 are (I assume) not mounted. Check if there is any files in the mount points itself. (Happend to me.) 
Now, you have to be VERY careful.

If you are not sure, unmount those two drives. Make ABSOLUTELY SURE they are NOT mounted.
Then delete the mount points.

3. Create the mount points again.

4. Reboot.

5. Come back here afterwards.

---

### Post by Bert Mariën on 2007-04-14
AGAIN: Make ABSOLUTELY SURE that the drives are not mounted, are you shall loose anything on the drives. (Also happened to me.)

---

### Post by reuben on 2007-04-14
Thanks, didn't resolve it tho.

There's no UUID for either of these drives in the db. 

If I do mount /mm1, for example, I get:

mount: special device /dev/disk/by-uuid/e19a4234-d7e3-45a7-b369-b6c1724ba0c6 does not exist

Interestingly, it looks like these drives are mapped by path, but not UUID or ID:

reuben@mediabox:/dev/disk/by-uuid$ ls /dev/disk/by-path/
pci-0000:00:08.0-scsi-0:0:0:0        pci-0000:00:08.0-scsi-0:0:0:0-part2  pci-0000:00:08.0-scsi-0:0:0:0-part6  pci-0000:00:08.0-scsi-1:0:0:0
pci-0000:00:08.0-scsi-0:0:0:0-part1  pci-0000:00:08.0-scsi-0:0:0:0-part5  pci-0000:00:08.0-scsi-0:0:0:0-part7  pci-0000:00:08.0-scsi-1:0:1:0
reuben@mediabox:/dev/disk/by-uuid$ ls /dev/disk/by-id/
scsi-1ATA_MAXTOR_4K040H2_672122700722        scsi-1ATA_MAXTOR_4K040H2_672122700722-part2  scsi-1ATA_MAXTOR_4K040H2_672122700722-part6
scsi-1ATA_MAXTOR_4K040H2_672122700722-part1  scsi-1ATA_MAXTOR_4K040H2_672122700722-part5  scsi-1ATA_MAXTOR_4K040H2_672122700722-part7
reuben@mediabox:/dev/disk/by-uuid$ ls /dev/disk/by-uuid/
0aeed028-94da-11d9-88ec-bda3b4dd8f69  99e436a5-6a3f-4932-b85a-70fb263b4afd  b41e32a6-4367-47ab-8885-01974ca0fb27  c7d10a87-3e04-4fbe-83ef-7e0a5541eb64

---

### Post by Bert Mariën on 2007-04-14
Wel, you can try to mount them by one of the 3 other options besides UUID. I guess there ain't no harm in trying.

I won't be on today no more though. I go to sleep for a while. Catch some ZZZZZ's

---

### Post by reuben on 2007-04-14
My bad; the extra ones in by-path were the cd drives. 

I would mount by label if I knew the labels :(

---

### Post by reuben on 2007-04-14
Two part workaround;

1) edit /etc/fstab to refer to devices by names rather than UUID (i.e. /dev/hdb)
2) reboot and use older kernel (kernel-2.6.20-12)

I updated [https://bugs.launchpad.net/ubuntu/+bug/106408](https://bugs.launchpad.net/ubuntu/+bug/106408) to reflect this information

---

### Post by Chazall1 on 2007-04-14
My /home partition will not mount at boot or when trying to mount it directly. All my other partitions mount, NTFS, Fat 32 and my External HD. I ran this,
ls /dev/disk/by-uuid/ -alh
Here is the Output:
drwxr-xr-x 2 root root 140 2007-04-14 18:07 .

drwxr-xr-x 6 root root 120 2007-04-14 14:04 ..

lrwxrwxrwx 1 root root  17 2007-04-14 18:04 07D4-0C0C -> ../../mapper/sdb1

lrwxrwxrwx 1 root root  10 2007-04-14 18:07 18c79eac-b4e4-4fea-a502-786ce82af86e -> ../../sda5

lrwxrwxrwx 1 root root  17 2007-04-14 18:04 8bd36f06-7967-47e4-9933-669abf52b03f -> ../../mapper/sda6

lrwxrwxrwx 1 root root  17 2007-04-14 18:04 ae513c0e-9646-47f3-8ffe-17c18555b26b -> ../../mapper/sda7

lrwxrwxrwx 1 root root  17 2007-04-14 18:04 CAF012F3F012E58B -> ../../mapper/sdb2


sda5 is my /home partition that will not mount. All the other partitions have ../../mapper/ before the partition? How can I configure ../../mapper for my home sda5???

Here is my fstab:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda6 :
UUID=8bd36f06-7967-47e4-9933-669abf52b03f / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=18c79eac-b4e4-4fea-a502-786ce82af86e /home ext3 defaults 0 2
# /dev/hdb1 -- converted during upgrade to edgy
#UUID=07D4-0C0C /media/hdb1  vfat iocharset=utf8,umask=000     0       0
# /dev/hdb2 -- converted during upgrade to edgy
UUID=CAF012F3F012E58B /media/hdb2 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb3 -- converted during upgrade to edgy
#/dev/hdb3   /media/hdb3  vfat iocharset=utf8,umask=000     0       0
#/dev/hda7 
UUID=ae513c0e-9646-47f3-8ffe-17c18555b26b	none swap sw 0 0
/dev/cdrom   /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb2 /mnt/windows ntfs-3g defaults 0 0

Any Ideas ?
Thanks

---

### Post by reuben on 2007-04-14
This bug is tracking the same issue:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106418](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106418)

---

### Post by Chazall1 on 2007-04-14
I had the swap issues before I updated to the latest kernel. Swap is fixed, just cant mount my /home. I am on Feisty now, my system seems to function very well, can I continue to function this way??????

Thanks

---

### Post by pedalwrench on 2007-04-14
Sorta worked for me...

I did the following:
```

ls -l /dev/disk/by-uuid/
```

which the output was:

```
lrwxrwxrwx 1 root root 10 2007-04-14 15:57 20b7f811-f6c8-4f91-a0ce-fcb940f412e5 -> ../../sdb1

lrwxrwxrwx 1 root root 10 2007-04-14 15:57 b061d32f-165d-4cb7-bff7-b71567d973ee -> ../../sda1

lrwxrwxrwx 1 root root 10 2007-04-14 15:57 b414eca8-78ac-44b2-a66b-39f58adbf4c4 -> ../../sdc5

lrwxrwxrwx 1 root root 10 2007-04-14 15:57 b52478d8-c28e-4f65-b9d1-42ed0d085944 -> ../../sdd1

lrwxrwxrwx 1 root root 10 2007-04-14 15:57 bc2a5c59-0f55-44c9-ba39-8b1472c02459 -> ../../sdc1
```

You will notice that I had 2 sdc's (1 and 5)

SDC1 is my root, and SDC5 is my swap.

I have 4 drives in my machine, 1 root, 1 home, 1 docs, 1 other

I knew that the Root drive and the Home drive were on the same IDE chain [old hda and hdb] and that the Docs drive and Other drive were on another IDE chain [old hdd and hde] so I did some sleuthing and figured the following out:

SDC = Root
SDD = Home
SDA = Docs
SDB = Other

It is kind of weird that the kernel mod changes them from a HDA [etc] to SDA [etc].

Is this the way things are going or is it just my Nforce chipset?

anyway it works. thanks for the help.:D

EDIT: forgot to add my fstab for others to see
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=bc2a5c59-0f55-44c9-ba39-8b1472c02459 /               ext3    defaults,erro$
# /dev/hda5
UUID=b414eca8-78ac-44b2-a66b-39f58adbf4c4 none            swap    sw           $
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0


# My Drives
#/dev/sdd1
UUID=b52478d8-c28e-4f65-b9d1-42ed0d085944 /home         ext3 defaults 0 0
#/dev/sda1
UUID=b061d32f-165d-4cb7-bff7-b71567d973ee /media/docs   ext3 defaults 0 0
#/dev/sdb1
UUID=20b7f811-f6c8-4f91-a0ce-fcb940f412e5 /media/other  ext3 defaults 0 0

```

---

### Post by Bert Mariën on 2007-04-15
> **reuben said:**
> My bad; the extra ones in by-path were the cd drives. 

I would mount by label if I knew the labels :(

You might find some extra information here:

/dev/.udev/failed

I can't see (because all my drives load) what information might be in here, but I assume the just information of your partitions (e.g. UUID etc) might be in here. Perhaps even a report describing the reason why those partitions weren't mounted.

---

### Post by Bert Mariën on 2007-04-15
> **reuben said:**
> My bad; the extra ones in by-path were the cd drives. 

I would mount by label if I knew the labels :(

 Here you should find all the information you need: disks by ID, by LABEL, by PATH, by UUID

/dev/.udev/names

---

### Post by Docter on 2007-04-20
Yep I had the same problem too. My hda's were changed to sda's and my hdc's were changed to sdb's.. Feisty made new labels in MTAB for everything except my swap. I've edited the fstab and mtab files and it seems to be holding.


Such a micro$oft thing to do but I shouldn't complain because I'm happy really.

---

### Post by Bert Mariën on 2007-04-20
So it work for you (editing mtab and fstab)? 
Glad at least it works for some people...
:)

---

### Post by solderhead on 2007-04-21
I've also got the problem with disappearing drives.  My /dev/hda1, /dev/hda2, etc. all had to be changed to /dev/sda1, /dev/sda2, etc.

my CDROM drives have also disappeared, and I haven't figured out how to get them back yet.  I cannot mount /dev/hdc, even if I try to change the FSTAB entries to mount it as /dev/sdb or /dev/scd0.  can anyone tell me what i need to do to get my optical drives back?

```
cat /etc/fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
# Entry for /dev/sda2 :
UUID=dd2de25e-592a-48bf-bbd1-ec4e656c23c3 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=e73e6378-e165-49d1-8f05-6ffffc87e4b8 none swap sw 0 0
/dev/scd0 /media/cdrom0 ro,auto user,auto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
```

---

### Post by Bert Mariën on 2007-04-21
Just woke up. 
I see you mount everything to the /dev directory. Maybe it is worth a try to mount  into the /media directory.

It is also possible (happened to me) that your mount points aren't empty. Check it. If they aren't, you need to delete the mount points (as root) and create theme again. Be VERY sure that the drives of the mount points you want to delete aren't mounted at the time, otherwise you shall loose all your data.

---

### Post by solderhead on 2007-04-21
thanks for your help.

it looks like the mount points aren't already taken:
```
root@todland:/dev/.udev/names# mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
```

it would appear that the device nodes do not exist:
```
root@todland:/dev/.udev/names# vdir /dev/sc*
vdir: /dev/sc*: No such file or directory
```

would this suggest that the problem is more likely a bug in udev/kernel implementation than a user configuration issue?  i don't see that there's anything else that i can change.

---

### Post by Bert Mariën on 2007-04-21
Sorry, I'm rather busy at the moment (working in my garden).

I don't really know what to say/ There are many people that experience trouble with the drives.
But here is what works for me:

fstab
+++

# /etc/fstab: static file system information.
# also see /dev/.udev/db for UUID
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=83cc59ad-1c60-4c02-8915-853231518a4d / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=ec5c1db6-10da-4d4f-b6ad-12141c69a05d /home ext3 defaults 0 2
# Entry for /dev/hda6 :
UUID=d523d63e-a58a-464b-a080-12e393a2e734 none swap sw 0 0

# Entry for /dev/hda1 :
UUID=6C0A-982B /media/boot vfat user,rw,umask=0000 0 0
# Entry for /dev/hdb1 :
UUID=608C24B58C24881C /media/muziek ntfs-3g user,rw,umask=0000,locale=nl_BE.UTF-8 0 0
# Entry for /dev/hdb5 :
UUID=8AB4-9466 /media/beebab vfat user,rw,umask=0000 0 0
# Entry for /dev/hdb6 :
UUID=D00E-DF05 /media/bestanden vfat user,rw,umask=0000 0 0
# Entry for /dev/hdb7 :
UUID=21A983189E035BB5 /media/back-up ntfs-3g user,rw,umask=0000,locale=nl_BE.UTF-8 0 0
# Entry for /dev/hdb8 :
UUID=7AE892C7DDF7A165 /media/zip-bestanden ntfs-3g user,rw,umask=0000,locale=nl_BE.UTF-8 0 0
# Entry for /dev/sda1
UUID=AF9D16F6A214AAB9 /media/usb ntfs-3g user,rw,umask=0000,locale=nl_BE.UTF-8 0 0

/dev/hdc /media/sony udf,iso9660 user,noauto 0 0
/dev/hdd /media/lite-on udf,iso9660 user,noauto 0 0
/dev/ /media/floppy auto rw,user,noauto 0 0

+++ 

mtab
+++

# /etc/mtab

/dev/hda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-14-generic/volatile tmpfs rw 0 0
/dev/hda5 /home ext3 rw 0 0
/dev/hda1 /media/boot vfat rw,umask=0000 0 0
/dev/disk/by-uuid/608C24B58C24881C /media/muziek fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/hdb5 /media/beebab vfat rw,umask=0000 0 0
/dev/hdb6 /media/bestanden vfat rw,umask=0000 0 0
/dev/disk/by-uuid/21A983189E035BB5 /media/back-up fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/disk/by-uuid/7AE892C7DDF7A165 /media/zip-bestanden fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/disk/by-uuid/AF9D16F6A214AAB9 /media/usb fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
+++

Maybe this will help you.

---

### Post by solderhead on 2007-04-21
thanks for your help.  it looks like i got it fixed:

[http://ubuntuforums.org/showpost.php?p=2501270&postcount=64](http://ubuntuforums.org/showpost.php?p=2501270&postcount=64)

---

### Post by entropic_existence on 2007-04-23
Well I updated on Saturday and my fstab and mtab where fine in terms of the actual drives and partitions on my machine, yesterday one of my external drives was working fine in terms of hotplugging but today my other external drive and my usb drive were not hotplugging and automounting at all. I have edited my fstab and mtab so I can manually mount them but I'm hopping the automount issue will be resolved given that it was working in Dapper and Edgy. Its a small thing for more experienced users but it can be a real annoyance and pain.

---

### Post by Omegatron on 2007-04-24
Wait a second.  What is this UUID derived from?  If I backed up partitions using [dd]("http://en.wikipedia.org/wiki/Dd_(Unix)") onto my external drive would they have conflicting UUIDs?  What if they have different files now?  What if my two external drives are the exact same size?  Were the UUIDs just introduced in Feisty for the first time, or did Edgy use them too?

---

