---
title: "How to mount LVM2 on a new installation?"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by unix4linux on 2008-01-11
Hi All,

I was recently running kubuntu and had an LVM drive (sdb).  At the time my primary drive was sda.  Now, I reinstalled my machine with Ubuntu Server.  The question is, how to I mount my LVM2 drive on the new installation?  I can't do mount /dev/sdb1 because it's an LVM and specifying the nouuid option to mount them doesn't work either.

Thanks

---

### Post by unix4linux on 2008-01-12
Anyone have any thoughts?

---

### Post by unix4linux on 2008-01-12
Ok, the only way I was able to mount the drive or at least one volume is by restarting the server and mounting it like this:

[COLOR="Red"]mount -a -w -t reiserfs /dev/Media/music /mnt/music[/COLOR]

then I:

[COLOR="Red"]cd /mnt/music[/COLOR] and everything is there

Now, I can d anything like cp the files over to a new drive or change their permissions.  I get permission denied even as root.  Here is what I get from what I do:

[COLOR="Red"]root@www:/mnt/music/pc_backup# ls -l
total 0
?--------- ? ? ? ?                ? etc.tar.gz
?--------- ? ? ? ?                ? home.tar.gz
?--------- ? ? ? ?                ? opt.tar.gz
root@www:/mnt/music/pc_backup# chmod 777 *
chmod: cannot access `etc.tar.gz': Permission denied
chmod: cannot access `home.tar.gz': Permission denied
chmod: cannot access `opt.tar.gz': Permission denied[/COLOR]

Any thoughts?

Please remember that this was an LVM or is an LVM drive and I am trying to retrieve my data out of it

---

### Post by scxtt on 2008-01-12
1st, are you sure it's formatted as reiser?
what do you get for commands like pvscan,vgscan,lvscan?
are the right kernel modules loaded (dm_*)?

---

### Post by unix4linux on 2008-01-13
Ok, so I made sure the module was loaded by probing dm-mod.  After I did that, I was able right away to just do:

[COLOR="Red"]mount /dev/Media/music /mnt/music[/COLOR]

I was even able to see that the files in /mnt/music no longer had question marks as permissions.  I then tried to copy a file from /mnt/music /home/myhome and it took a few seconds before returning an input/output error.

I then unmounted the lv and tried to mount it like this instead:

[COLOR="Red"]mount -t reiserfs /dev/Media/music /mnt/music[/COLOR]

but it complained about wrong filesystem type.  I am pretty sure that when I formatted the drive I did it as reiserfs.

I then proceeded to try and mount it as I did the first time:

[COLOR="Red"]mount /dev/Media/music /mnt/music[/COLOR]

but this time it complained that I need to specify a filesystem:

[COLOR="Red"]root@www:/mnt# mount /dev/Media/music /mnt/music/
mount: you must specify the filesystem type[/COLOR]

When I run lvscan, pvscan, and vgscan this is what I get:

[COLOR="Red"]root@www:/mnt# pvscan
  /dev/Media/music: read failed after 0 of 4096 at 214748299264: Input/output error
  /dev/Media/music: read failed after 0 of 4096 at 0: Input/output error
  /dev/Media/pictures: read failed after 0 of 4096 at 161061208064: Input/output error
  /dev/Media/pictures: read failed after 0 of 4096 at 0: Input/output error
  /dev/Media/videos: read failed after 0 of 4096 at 123480244224: Input/output error
  /dev/Media/videos: read failed after 0 of 4096 at 0: Input/output error
  /dev/Media/docs: read failed after 0 of 4096 at 813629440: Input/output error
  /dev/Media/docs: read failed after 0 of 4096 at 0: Input/output error
  /dev/sdb1: read failed after 0 of 1024 at 500105150464: Input/output error
  /dev/sdb1: read failed after 0 of 2048 at 0: Input/output error
  PV /dev/sda5   VG www   lvm2 [74.27 GB / 0    free]
  Total: 1 [74.27 GB] / in use: 1 [74.27 GB] / in no VG: 0 [0   ]
root@www:/mnt# lvscan
  /dev/Media/music: read failed after 0 of 4096 at 214748299264: Input/output error
  /dev/Media/music: read failed after 0 of 4096 at 0: Input/output error
  /dev/Media/pictures: read failed after 0 of 4096 at 161061208064: Input/output error
  /dev/Media/pictures: read failed after 0 of 4096 at 0: Input/output error
  /dev/Media/videos: read failed after 0 of 4096 at 123480244224: Input/output error
  /dev/Media/videos: read failed after 0 of 4096 at 0: Input/output error
  /dev/Media/docs: read failed after 0 of 4096 at 813629440: Input/output error
  /dev/Media/docs: read failed after 0 of 4096 at 0: Input/output error
  /dev/sdb1: read failed after 0 of 1024 at 500105150464: Input/output error
  /dev/sdb1: read failed after 0 of 2048 at 0: Input/output error
  ACTIVE            '/dev/www/root' [71.20 GB] inherit
  ACTIVE            '/dev/www/swap_1' [3.07 GB] inherit
root@www:/mnt# vgscan
  Reading all physical volumes.  This may take a while...
  /dev/Media/music: read failed after 0 of 4096 at 214748299264: Input/output error
  /dev/Media/music: read failed after 0 of 4096 at 0: Input/output error
  /dev/Media/pictures: read failed after 0 of 4096 at 161061208064: Input/output error
  /dev/Media/pictures: read failed after 0 of 4096 at 0: Input/output error
  /dev/Media/videos: read failed after 0 of 4096 at 123480244224: Input/output error
  /dev/Media/videos: read failed after 0 of 4096 at 0: Input/output error
  /dev/Media/docs: read failed after 0 of 4096 at 813629440: Input/output error
  /dev/Media/docs: read failed after 0 of 4096 at 0: Input/output error
  /dev/sdb1: read failed after 0 of 1024 at 500105150464: Input/output error
  /dev/sdb1: read failed after 0 of 2048 at 0: Input/output error
  Found volume group "www" using metadata type lvm2[/COLOR]

Any other ideas?  Is there another module I need to have loaded besides dm-mod?

Thanks for your help.  I got closer this time but not quite there yet :confused:

---

### Post by scxtt on 2008-01-13
what's the output of:

**sudo fdisk -l**
**ls -l /dev/mapper/**

you should be able to use **sudo blkid /dev/mapper/<mapped device>** to tell you what type of f/s it is:
```
:> sudo blkid /dev/mapper/vg00-root 
/dev/mapper/vg00-root: LABEL="root" UUID="123f0627-234c-400e-bd32-88f49c2ea1f7" SEC_TYPE="ext2" [COLOR="Red"]TYPE="ext3"[/COLOR]
```

here's the dm_* modules that get loaded on my box that is all LVM:
```
:> sudo lsmod | grep dm
[sudo] password for scxtt:
dm_mirror              25472  0 
dm_snapshot            19656  0 
dm_mod                 67440  21 dm_mirror,dm_snapshot
```

---

### Post by unix4linux on 2008-01-13
Hmmm, I have checked all of the options above and everything seems fine.  I can mount the filesystem with no problem but I continue to get input/output errors when trying to access any of the files in my lvm.

If I try to mv or cp a file it will say something like:

[COLOR="Red"]mv: reading `thisfile/directory1/sample.jpg': Input/ouput error[/COLOR]

It says that for any file or directory I try to manipulate.

Here is the output of the suggested options:

[COLOR="Red"]root@www:/home/user1# fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfb6dfb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        9726    77875087+   5  Extended
/dev/sda5              32        9726    77875056   8e  Linux LVM

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00046c78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   8e  Linux LVM

root@www:/home/user1# ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 63 2008-01-13 10:54 control
brw-rw---- 1 root disk 254,  3 2008-01-13 10:54 Media-docs
brw-rw---- 1 root disk 254,  0 2008-01-13 10:54 Media-music
brw-rw---- 1 root disk 254,  1 2008-01-13 10:54 Media-pictures
brw-rw---- 1 root disk 254,  2 2008-01-13 10:54 Media-videos
brw-rw---- 1 root disk 254,  4 2008-01-13 10:54 www-root
brw-rw---- 1 root disk 254,  5 2008-01-13 10:54 www-swap_1

root@www:/home/user1# ls -l /dev/mapper/Media-music
brw-rw---- 1 root disk 254, 0 2008-01-13 10:54 /dev/mapper/Media-music

root@www:/home/user1# blkid /dev/mapper/Media-music
/dev/mapper/Media-music: UUID="baebda81-d730-43b6-83b5-b3f605c49b4c" TYPE="reiserfs"

root@www:/home/user1# lsmod | grep dm
dm_crypt               14984  0
dm_mirror              24320  0
dm_snapshot            18980  0
dm_mod                 58816  16 dm_crypt,dm_mirror,dm_snapshot[/COLOR]

This is going to be very bad if I can't recover any data :mad:

I appreciate the help so far though :-D

---

### Post by scxtt on 2008-01-14
try running **fsck.reiserfs** on the LVM giving you trouble - probably best that it isn't mounted ...

---

### Post by unix4linux on 2008-01-14
Ok, I ran fsck.reiserfs on my lvms and I get an error:

[COLOR="Red"]bread: Cannot read the block (2) : (Input/output error) .[/COLOR]

It says that with of course a different block number for each of my lvm which I have 4 of them.  So looks like just because I installed a new O/S the drive became bad.  This is strange because the drive is new.  I have only had it for about a month.

Is there anyway to recover data from a drive with bad blocks?

[COLOR="Red"]root@www:~# fsck.reiserfs /dev/Media/music
reiserfsck 3.6.19 (2003 [www.namesys.com](www.namesys.com))

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to [email]reiserfs-list@namesys.com[/email], **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  [www.namesys.com/support.html](www.namesys.com/support.html). **
*************************************************************

Will read-only check consistency of the filesystem on /dev/Media/music
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes

The problem has occurred looks like a hardware problem. If you have
bad blocks, we advise you to get a new hard drive, because once you
get one bad block  that the disk  drive internals  cannot hide from
your sight,the chances of getting more are generally said to become
much higher  (precise statistics are unknown to us), and  this disk
drive is probably not expensive enough  for you to you to risk your
time and  data on it.  If you don't want to follow that follow that
advice then  if you have just a few bad blocks,  try writing to the
bad blocks  and see if the drive remaps  the bad blocks (that means
it takes a block  it has  in reserve  and allocates  it for use for
of that block number).  If it cannot remap the block,  use badblock
option (-B) with  reiserfs utils to handle this block correctly.

bread: Cannot read the block (2): (Input/output error).

Aborted[/COLOR]

---

### Post by scxtt on 2008-01-16
you could use **badblocks** to check the device for bad blocks ... then if you actually have some, we'll have to see what options you have from there ...

---

### Post by unix4linux on 2008-01-16
Hi,

I am not going to say that I fixed the problem but more like cheated my way around the problem.  I did run

[COLOR="Red"]badblocks -s /dev/sdb1[/COLOR]

prior to your posting and it was reporting that every block was bad.  So here is what I did and I don't understand why that worked:

[COLOR="Red"]Shutdown the pc
removed the primary boot drive out
moved the secondary drive to the first device area to make it sda instead of sdb
booted with kubuntu livecd 7.10 gutsy
apt-get install lvm
apt-get install dm-mod
modprobe dm-mod
modprobe dm-crypt
vgchange -ay
mount -w -t reiserfs /dev/Media/music /mnt/music
    "                                              ../../docs /mnt/docs
    "                                             ../../videos /mnt/videos
    "                                             ../../pictures /mnt/pictures[/COLOR]

Then, I was able to get all of my data out of there and copied to another drive and the data seems to be working just fine with no input/output errors any longer.

Now, this didn't work with the Ubuntu 7.10 Gutsy server cd but only worked with the kubuntu livecd.  And as you know, it didn't work while the O/S was installed.  Why would that be?  Why would it have only worked with the kubuntu livecd?

Does that mean that LVM's can only be recovered from the originating O/S?  What backup solutions can be suggested so that I don't go through this nightmare again?

Thanks a bunch for all the help

---

### Post by scxtt on 2008-01-16
> **unix4linux said:**
> Now, this didn't work with the Ubuntu 7.10 Gutsy server cd but only worked with the kubuntu livecd.  And as you know, it didn't work while the O/S was installed.  Why would that be?  Why would it have only worked with the kubuntu livecd?

Does that mean that LVM's can only be recovered from the originating O/S?  What backup solutions can be suggested so that I don't go through this nightmare again?sometimes f/s manipulation can't be done while the f/s is mounted ... no idea why the server cd wouldn't work, unless it's missing some utilities - but if you install kubuntu 6.06, there's no reason why an ubuntu 7.10 disk wouldn't work to do what you were doing (and vice versa) ...

you can take lv snapshots and then back those up ... you just create a "snapshot" LV that co-exists w/ what it's a snapshot of, then you can back it up while the original is *live* ... it's pretty cool.

sometime i'll have to mess w/ the virtual LVM disks i have and move them around between different VMs - see if i have similar problems ... my physical LVMs are staying put ;)

---

### Post by unix4linux on 2008-01-16
Yeah...this was a little crazy and confusing but I def. appreciate your help :-D.  As I type this, my data is now being restored to my new PV/VG :popcorn:

I had moved it out to a temp place after I was able to get it out of that crazy drive while I fixed it.

Thanks again!!!!

---

### Post by unix4linux on 2008-01-17
OMFGGGGGGGGGGGGG

I restored all the data and everything was fine.  The data was readable.  The moment I created a file share with samba the permissions on the drive all went back to question marks like before and now I am getting input/output errors again!!!....seriously..WTF!!!!

I don't think samba is the real cause of it because it was fine for a little while and when I was having this problem before I had never done anything with Samba...this is the first time I shared it with Samba.  I think when I tried to read the folder through my windows then it started to blow chunks!!!

[COLOR="Red"]root@www:/mnt/music# vgchange -ay
  /dev/sdb1: read failed after 0 of 1024 at 500105150464: Input/output error
  /dev/sdb1: read failed after 0 of 2048 at 0: Input/output error
  2 logical volume(s) in volume group "www" now active[/COLOR]

---

### Post by unix4linux on 2008-01-17
As I was trying to take the hard drive out to kick a field goal with it I noticed the sata cable was damaged....I changed it with another I had and it came up just fine....I hope that was it and if so I just did all that crap for nothing!!!!!...oh well...so much for thinking outside the box, right??](*,)

---

