---
title: "My device are now &quot;sda&quot; than &quot;hda&quot;"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by chakkaradeep on 2007-04-10
Hi All,

I dont have SATA drives in my laptop. I recently upgraded from Edgy Eft to Fiesty using the Upgrade Manager. The Edgy was holding /dev/hda and once it upgraded, it has changed to /dev/sda. Not sure why its showing as /dev/sda.

Any idea ?

---

### Post by hardyn on 2007-04-10
yup... they are... 

there have been many posts about this... IDE drives are now handled by the SATA driver... this is normal.

---

### Post by chakkaradeep on 2007-04-10
> **hardyn said:**
> yup... they are... 

there have been many posts about this... IDE drives are now handled by the SATA driver... this is normal.

Thanks :)

---

### Post by frodon on 2007-04-10
BTW, i wondered if you got any issues related to this upgrading to feisty or if you were just wondering why the name are sda now instead of hda.
I'm trying to know if the update manager automatically update the fstab and grub.list to match the new names or if you have to update it by hand.

---

### Post by chakkaradeep on 2007-04-10
> **frodon said:**
> BTW, i wondered if you got any issues related to this upgrading to feisty or if you were just wondering why the name are sda now instead of hda.
I'm trying to know if the update manager automatically update the fstab and grub.list to match the new names or if you have to update it by hand.

I didnt do any changes to fstab manually. Fiesty is kewl and wokring without any flaws. Its just I was wondering why my hard drive are named sda now than hda. As of now, no issues. fstab is using UIDs but its still the edgy fstab, due to the usage of UIDs, i think it does not differentiate hda or sda. Below is my fstab file,

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=b4456ccd-3ae9-44fd-9499-0a33fbae8683 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=063C8EAC3C8E9679 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
# UUID=95fbbc8f-fb35-4c75-933a-8f5d6273162d /media/hda3     ext3    defaults        0       1
# /dev/hda5
UUID=8430B4C830B4C28A /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=CAC08761C087531D /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda7
 UUID=f6ba4a42-67e2-4d68-acc5-a1424e1d5082 none            swap    sw              0       0
#/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Hope am clear :) I think it would fail it the fstab is going to contain /dev/hda(x) entries, but i dont want to take that risk :)

---

### Post by frodon on 2007-04-10
> **chakkaradeep said:**
> 
Hope am clear :) I think it would fail it the fstab is going to contain /dev/hda(x) entries, but i dont want to take that risk :)Thanks exactly what i wanted to know, i'm thinking about a warning to check that the fstab use UUID before upgrading just to avoid fstab problems rebooting after the upgrade because as you said it will fail to boot for those who use fstab files without UUID description.

---

### Post by lexxonnet on 2007-04-10
Hmm... since I upgraded, I've been having problems with one of my ext3 partitions though. I seem to get fsck running every time on startup, and I get a lot of  "short reads". This has been the case with every kernel since 2.6.20-11, and I'm still using 11(which gives me the normal PATA drivers). I need to try 14 to see if the issue has been fixed though...

---

### Post by frodon on 2007-04-10
It won't IMO because the SATA drivers are now used for IDE drives, so it's easier to edit your fstab file to use UUID instead of /dev/hdx, doing this you won't have any problem related to this anymore.
The following command will list all the UUID of your partitions, then you just have to put them instead of the /dev/hdx in your fstab file :
```
sudo ls -l /dev/disk/by-uuid/
```Take the chakkaradeep's fstab file as example to edit your fstab file.

---

### Post by chakkaradeep on 2007-04-10
> **frodon said:**
> 
```
sudo ls -l /dev/disk/by-uuid/
```

Or,

```
sudo vol_id /dev/<partition>
``` :)

---

### Post by jerrylamos on 2007-04-10
Well, with CD Live Kubuntu 20070402 on an IBM NetVista, I was trying to see if "persistent" worked so I did a df -h and noticed the USB wasn't /dev/sda1 but /dev/sdb1  ??  

Somewhere In the process of trying to see if "persistent" would work I formatted what I thought was casper-rw with the usual command line (there isn't any Ubuntu menu for making "persistent" like competitive Linux's have):

mkfs.ext3 -b 4096 -L casper-rw /dev/sda1 

which reformatted Windows XP which was on hda1.

Oops.  I re-installed XP and 'm still re-constructing the data files.....

Thanks for the warning.....

On a different computer this installed Ubuntu all up to date, hda1 is still hda1 ??

And the USB is still /dev/sda1 ??

Cheers, Jerry :confused:

---

### Post by chakkaradeep on 2007-04-10
> **jerrylamos said:**
> 
On a different computer this installed Ubuntu all up to date, hda1 is still hda1 ??

And the USB is still /dev/sda1 ??



As far as i know, this happens only in Fiesty

---

### Post by rajeev1204 on 2007-04-10
Hi 

i have a problem mounting my cdrom . 
Actuallly if its  a ***vcd*** it doesnt mount . Only data cd and dvd auto mount .

Also 2 cdroms and 2 floppys are listed under /media after a particular update. 

when i say mount /dev/cdrom it says no /dev/scd0 entry in fstab or mtab


Also names of devices seem to have changed too 

from hdc to sdc or something

---

### Post by chakkaradeep on 2007-04-10
> **rajeev1204 said:**
> Hi 
i have a problem mounting my cdrom . 
Only data cd and dvd auto mount .


Once it mounts the data cd, type in **mount** in the terminal and find wat it has mounted for the cdrom. Try the same for mounting vcds using the command **mount -v <device> <dest>**. Remember the **-v** option for verbose mode so that you could check whats happening.

---

### Post by rajeev1204 on 2007-04-10
ok 

i added a new line to fstab /dev/scd0  /media/cdrom  etc etc . 

So now only vlc recognises the path correctly and plays it .
gxine just crashes .

Anyways i have a question .

In my fstab entries , except this new entry rest all are hashed out .

I thought commenting out a line means it is ignored :confused: :confused: 

So how come they too are mounted on boot ?

Also why dvd is automounted without entry in fstab and vcd is not? Maybe its a kernel bug

even data cd works . only video cd wont automount . The above line does it now. 


All this happened after the first partial upgrade

---

### Post by chakkaradeep on 2007-04-10
> **rajeev1204 said:**
> 
In my fstab entries , except this new entry rest all are hashed out .


Can you please paste your /etc/fstab file here?

---

### Post by psyke83 on 2007-04-10
There's two issues here:

1. Drives are using the new libata subsystem, meaning that IDE devices appear as SCSI. This is normal, and all your drives should still be working.

2. Feisty now uses UUID's to identify and mount disks. You can check a drive's UUID identifier with "sudo vol_id /dev/sda1", for example - it's unique to each partition. Now here's the problem: try to run "sudo vol_id /dev/sdc0" when there's no CD present in your drive - UUID won't work for optical media. You have to manually specify optical devices by device name in /etc/fstab. 

If you upgraded from Edgy or pre-beta Feisty, your /etc/fstab may incorrectly point towards /dev/hdc for your optical drive, but it needs to be something like /dev/sdc0, due to point 1 above. That should resolve most people's issues with optical drives at the moment.

---

### Post by theWrkncacnter on 2007-04-10
> **frodon said:**
> BTW, i wondered if you got any issues related to this upgrading to feisty or if you were just wondering why the name are sda now instead of hda.
I'm trying to know if the update manager automatically update the fstab and grub.list to match the new names or if you have to update it by hand.

Mine got changed too, except the cd drive did stop working when I upgraded to feisty. I tried manually editing fstab, but had no luck. Any ideas on how to fix this? I'm not sure what the device name of the CD drive is. In my fstab I called it /dev/sdb.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=e7a84da0-d3e5-4cd3-b69e-66127583f09d / ext3 defaults,user_xattr,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=8afa23d2-fc5a-4fe9-b108-3b5424cfe100 none swap sw 0 0
# old cdrom entry -- /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb	/media/cdrom0   udf,iso9660 user,auto     0       0
/dev/sda1	/media/windows	ntfs-3g	defaults,locale=en_US.utf8	0	0	
/dev/sda3        none        swap        sw     0     0

When I try to mount it it does this
> $ mount /media/cdrom
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

> $ dmesg | tail
[ 6078.280744] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[ 6095.351237] ath0: no IPv6 routers present
[ 6571.038078] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[ 6571.201518] ADDRCONF(NETDEV_UP): ath0: link is not ready
[ 6573.810800] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[ 6589.463826] ath0: no IPv6 routers present
[ 7781.228883] UDF-fs: No partition found (1)
[ 7781.229511] isofs_fill_super: bread failed, dev=sdb, iso_blknum=16, block=32
[ 7907.726486] UDF-fs: No partition found (1)
[ 7907.730472] isofs_fill_super: bread failed, dev=sdb, iso_blknum=16, block=32


---

### Post by psyke83 on 2007-04-10
theWrkncacnter,

Why did you choose /dev/sdb? Your CD-ROM device is /dev/scd* (most likely /dev/scd0). See my earlier post for an explanation, please.

---

### Post by theWrkncacnter on 2007-04-10
Sorry, my /dev folder doesn't have anything close to /scd* in it! What should I do? (hdc isn't there either)

ls /dev/
...
rtc
sda
sda1
sda2
sda3
sdb
sequencer
...

are you SURE I'm using the wrong device?

---

### Post by psyke83 on 2007-04-10
theWrkncacnter,

Can you please post the output of:
```
$ dmesg | grep -i cd-rom
```

---

### Post by theWrkncacnter on 2007-04-10
"dmesg | grep -i cd-rom" gives no output : (
And "df -h" doesn't mention it either : ( Is this some kind of driver problem?

---

### Post by ciscosurfer on 2007-04-10
> **rajeev1204 said:**
> [...]Anyways i have a question.

In my fstab entries, except this new entry rest all are hashed out .
I thought commenting out a line means it is ignored :confused: :confused: 

So how come they too are mounted on boot?[...]I am having the same issue with my fstab (commenting out a line, but the partition or drive still mounts anyway).  Would love to hear suggestions on this. :-)

---

### Post by psyke83 on 2007-04-10
> **ciscosurfer said:**
> I am having the same issue with my fstab (commenting out a line, but the partition or drive still mounts anyway).  Would love to hear suggestions on this. :-)

Feisty mounts drives using UUID (a long alphanumeric sequence that represents your partitions). When you look in /etc/fstab, the commented lines are essentially a human guide to help us see what  partitions each UUID represents.

Everybody, *don't* start uncommenting those lines, it will make things worse (potentially causing every partition to be mounted twice).

---

### Post by psyke83 on 2007-04-10
theWrkncacnter,

Try:
```
$ sudo modprobe sr_mod
$ sudo modprobe cdrom
$ dmesg | tail
```

Paste the output of the final command here.

Another suggestion: download either the Feisty beta LiveCD or the latest daily build, boot from it and see how it handles your CD-ROM drive. I have a feeling that something on your system didn't upgrade cleanly after the libata transition (the past few kernels have been alternating between hd* and sd* naming of drives).

By the way, "df -h" doesn't show optical drives unless there's media loaded and it's mounted; df works with filesystems, *not* drives.

---

### Post by ciscosurfer on 2007-04-10
> **psyke83 said:**
> Feisty mounts drives using UUID (a long alphanumeric sequence that represents your partitions). When you look in /etc/fstab, the commented lines are essentially a human guide to help us see what  partitions each UUID represents.

Everybody, *don't* start uncommenting those lines, it will make things worse (potentially causing every partition to be mounted twice).You're not quite following me.  I know all about UUID's and how they work.  My issue is this: I am adding in a # in front of a line that I don't want to mount.  This has always worked before, this is the way I've always done it, this is the way I code, etc., etc. (this is called commenting out a line...as an aside, I realize that this is probably a matter of semantics: I have always referred to lines that I add a comment to as "commenting out" and perhaps you thought I was actually removing the hash mark...but I wasn't.  Sorry for the digression.)  Meaning, that something other than /etc/fstab is calling this partition that I've specified not to start up at boot, to mount at boot.

---

### Post by psyke83 on 2007-04-10
ciscosurfer,

Ah sorry, I misunderstood. That is pretty strange indeed. Checking launchpad, I found a potential bug relating to this issue: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/73126](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/73126)

---

### Post by theWrkncacnter on 2007-04-10
$ sudo modprobe sr_mod
$ sudo modprobe cdrom
$ dmesg | tail
returned nothing relevant
> [21775.050565] ath0: no IPv6 routers present
[21873.526444] ADDRCONF(NETDEV_UP): ath0: link is not ready
[21875.807538] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[21892.539767] ath0: no IPv6 routers present
[23817.705724] ADDRCONF(NETDEV_UP): ath0: link is not ready
[23818.008552] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[23836.635821] ath0: no IPv6 routers present
[23937.182427] ADDRCONF(NETDEV_UP): ath0: link is not ready
[23939.771121] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[23957.035071] ath0: no IPv6 routers present

Will try the live cd

---

### Post by ciscosurfer on 2007-04-10
> **psyke83 said:**
> ciscosurfer,

Ah sorry, I misunderstood. That is pretty strange indeed. Checking launchpad, I found a potential bug relating to this issue: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/73126](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/73126)Thanks for the bug link.  Looking at it, I believe I can modify it to suit my needs.  Curious though, why this wouldn't have already been incorporated into Feisty...

---

### Post by azelter on 2007-04-11
I recently upgraded to feisty and have had strange things going on with mounted partitions. In kernel 2.6.20-13 my root is /dev/hdb2 and /data is /dev/mapper/hdb3. In the fstab all the devices are refered to by UUID. I do not know why root is /dev/hdb2 and /data is /dev/mapper/... however when unning this kernel (2.6.20-13) the system seems to work as it should. 

When I boot into kernel 2.6.20-14, however, /dev/hdb2 is /dev/sda2 and /dev/mapper/hdb3 (which I think should just be /dev/hdb3) is /dev/sda3. This would be fine, except that /data then suffers from IO problems whar reading from the disk. Most of the information on the disk cannot be accessed as a result and then when I boot back in to 2.6.20-13 fsck has to run before the drive can be remounted.

Can anyone give me some leads as to what might be happening? Should I wait for a kernel update or is this a problem specific to this machine?

---

### Post by rajeev1204 on 2007-04-11
here is my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b5b45642-18fc-4e94-b360-332457368e87 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=b9ddc8c8-4904-45b4-8d3f-4a7aa8ca27f0 /home           ext3    defaults        0       2
#/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=45DD-A3F0  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=c32213ce-de3f-4aac-a69e-85482edfe15e none            swap    sw              0       0
#/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/scd0        /media/cdrom0     iso9660 user,noauto  0        0


One thing is clear --- the uuid line is not hashed and that is what is being loaded

that last line i have added cos it was not mounting my vcd . It automounts data cd and dvd fine . 

Also note i have hashed the /dev/hdb and dev/fd0 as that showed up as extra entries.

Iam still not sure i have added the /dev/scd0 line correctly cos only vlc plays it .

Totem never plays vcd and gxine crashes with segfault

---

### Post by theWrkncacnter on 2007-04-14
psyche83, and anyone else,
I tried the livecd, but I don't know how it treats cds, because it requires the cd to be in there to work, and I only have one cd drive.
Fstab doesn't have an entry for the cd drive.
Is there anything else I should try?

---

### Post by gregconquest on 2007-04-19
Is there a source for this transition from the old /dev/hda . . . to # /dev/sda (next line) UUID . . . .? I'm trying to make a guide for fstab at [http://ubuntuforums.org/showthread.php?p=2477107#post2477107]("http://ubuntuforums.org/showthread.php?p=2477107#post2477107") and I'd like to mention this fstab format transition and provide a good link.

I see several discussions and bug reports on the transition, but I can find nothing authoritative on what's going on.

Greg

---

### Post by frodon on 2007-04-19
Type this to get the UUID of all your partition :
```
sudo ls -l /dev/disk/by-uuid/
```Then you just have to edit your fstab and replace the "/dev/hdxX" by "UUID=b4456ccd-3ae9-44fd-9499-0a33fbae8683" where the number is the UUID which correspond to the partition.

---

### Post by Jhongy on 2007-04-19
I plan on adjusting a few partitions using gparted.

Will this change their UUIDs, meaning I'll have to update fstab each time?

---

### Post by Rui Pais on 2007-04-19
> **frodon said:**
> Type this to get the UUID of all your partition :
```
sudo ls -l /dev/disk/by-uuid/
```Then you just have to edit your fstab and replace the "/dev/hdxX" by "UUID=b4456ccd-3ae9-44fd-9499-0a33fbae8683" where the number is the UUID which correspond to the partition.

or if you want just the UUID of one specific partition you can use:
```
sudo vol_id -u /dev/sdXX
```
it's easier to read.

---

### Post by Rui Pais on 2007-04-19
> **Jhongy said:**
> I plan on adjusting a few partitions using gparted.

Will this change their UUIDs, meaning I'll have to update fstab each time?

You will need to edit it, if you change (format/resize/make new) some partition. 
Thats when partitions UUID change.

---

### Post by Jhongy on 2007-04-19
I hope the gparted LiveCD has vol_id available? I wonder if it also presents disks in /dev/disk/by-uuid? I assume it does?

---

### Post by Rui Pais on 2007-04-19
> **Jhongy said:**
> I hope the gparted LiveCD has vol_id available? I wonder if it also presents disks in /dev/disk/by-uuid? I assume it does?

the /dev/disk/by-uuid are made by the kernel. If gparted livecd as a kernel that supports UUID (any minimum recent kernel, from 2.6.17 i think, support it) will have them.

vol_id it's part of udev (and strangely it's available by another tool call volumeid, at least under ubuntu) 
The gparted liveCD should have at least udev version.

---

### Post by frodon on 2007-04-20
@chakkaradeep

I wonder one more thing, we all know that IDE drives are now handled by the SATA drivers and are now called sdx instead of hdx and that it's not a problem when you use UUID in your fstab.
We also know that the menu.list file use UUID by default but what about the device.map file which describe the disk referenced with hd0(x,x) for example in the menu.list.

Could you post your device.map file just to see if the upgrade renamed your drive in this file or if it don't matter if in this file the hard drive is still referenced as hdx.

Thanks for any insight brought on this (i'm curious :) )

---

### Post by chakkaradeep on 2007-04-20
> **frodon said:**
> 
Could you post your device.map file just to see if the upgrade renamed your drive in this file or if it don't matter if in this file the hard drive is still referenced as hdx.


Here you go 

```

(hd0)   /dev/hda
**(hd1)   /dev/sda**

```

I think it has added its part :) where I have showed with bold text.

---

### Post by frodon on 2007-04-20
Thanks chakkaradeep for the quick reply, you rock :KS

Ok so f i understand well the device.map modification is needed for GRUB to get the right partition path. And now my last question is :
Does your menu.list use hd0 or hd1 to reference your partition ?

BTW you have only one IDE drive right ?

Thanks chakkaradeep for your feedback, thanks to your replies i have improved my GRUB booting process understanding :).

---

### Post by chakkaradeep on 2007-04-20
> **frodon said:**
> Thanks chakkaradeep for the quick reply, you rock :KS

:) , no buddy, Ubuntu rocks :guitar: 

> **frodon said:**
> 
Ok so f i understand well the device.map modification is needed for GRUB to get the right partition path. And now my last question is :
Does your menu.list use hd0 or hd1 to reference your partition ?


Yes you are correct. But quite cofusing is now the menu.lst where I have still reference to only **hd0**

```

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=b4456ccd-3ae9-44fd-9499-0a33fbae8683 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

> **frodon said:**
> 
BTW you have only one IDE drive right ?


I use my laptop and have only one IDE (100 GB) :)

---

### Post by frodon on 2007-04-20
I guess that the IDE drive is referenced as sdx only once the kernel is booted and loaded and that at the GRUB step (no kernel loaded) it uses standard names. That would perfectly explain why you need UUID in the fstab (or sdx names) and only old names like for "root            (hdx,x)" in the menu.list file.

---

### Post by chakkaradeep on 2007-04-20
> **frodon said:**
> I guess that the IDE drive is referenced as sdx only once the kernel is booted and loaded and that at the GRUB step (no kernel loaded) it uses standard names. That would perfectly explain why you need UUID in the fstab (or sdx names) and only old names like for "root            (hdx,x)" in the menu.list file.

Yes :)

---

### Post by solderhead on 2007-04-21
I am also having trouble with the disappearing CDRW drive.  When performing the "mount -a" command as superuser, the following fstab entry resulted in the following error:

/etc/fstab line item:
```
/dev/hdc /media/cdrom0 ro,iso9660 user,auto 0 0
```

error message:
```
# mount -a
mount: special device /dev/hdc does not exist
```

after reading this thread, i changed the fstab entry to this:

```
/dev/scd0 /media/cdrom0 iso9660 user,noauto 0 0
```

after making this change, i have good news and bad news:  the good news is that i no longer receive the "special device does not exist" error.  the bad news is that the CDROM drive is still missing.

ideas?

---

### Post by chakkaradeep on 2007-04-21
> **solderhead said:**
> 
after reading this thread, i changed the fstab entry to this:

```
/dev/scd0 /media/cdrom0 iso9660 user,noauto 0 0
```

after making this change, i have good news and bad news:  the good news is that i no longer receive the "special device does not exist" error.  the bad news is that the CDROM drive is still missing.


I have an external dvd reader/writer and thats been recorded as **/dev/scd1** and **/dev/scd0**. This was a fresh install. 

But however, during my upgrade from edgy to feisty, it wasnt the same and I had to manually change the fstab for **/dev/scd1**

The upgrade process didnt add the changes for cd/dvd drives for me to fstab which i think is important.

---

### Post by solderhead on 2007-04-21
thanks for your help.

i have tried manually editing the fstab entries using /dev/scd0, and /dev/scd1.  neither one works.

although it appears that i have correctly edited the entries in /etc/fstab, it appears that there are no scd* nodes in the /dev directory.

---

### Post by chakkaradeep on 2007-04-21
> **solderhead said:**
> 
i have tried manually editing the fstab entries using /dev/scd0, and /dev/scd1.  neither one works.


Can you check by typing **sudo ls /dev/scd (tab key)** so that it displays some of the devices available and you could get to know if scd0 and scd1 exists. If you find them, please do,
**sudo mount /dev/scd(x) /media/cdrom** to check whether you can mount any dvd/cd drive.

---

### Post by Patrick K on 2007-04-21
I had to edit /etc/mtab to "sda" from "hda" as well as fstab. Just doing fstab didn't mount the partitions. Also, my hdc drive became sdb, so watch for that if you have more than one HD.

---

### Post by theWrkncacnter on 2007-04-21
> **chakkaradeep said:**
> Can you check by typing **sudo ls /dev/scd (tab key)** so that it displays some of the devices available and you could get to know if scd0 and scd1 exists. If you find them, please do,
**sudo mount /dev/scd(x) /media/cdrom** to check whether you can mount any dvd/cd drive.

I tried this, and confirmed that there are no entries in /dev starting with scd. What can I do?

---

### Post by chakkaradeep on 2007-04-21
> **theWrkncacnter said:**
> I tried this, and confirmed that there are no entries in /dev starting with scd. What can I do?

Ok, open the **Hardware Information** from **System-->Preferences-->Hardware Information** and try to find whether you can find your cd/dvd info. It should be there. Just to make sure that your CD drive is been identified.

And also, try opening K3B configuration where it scans for CD drives and reports back!

---

### Post by theWrkncacnter on 2007-04-21
I couldn't find anything in Hardware Information, and K3b couldn't either
> No CD/DVD writer found.
K3b did not find an optical writing device in your system. Thus, you will not be able to burn CDs or DVDs. However, you can still use other K3b features like audio track extraction or audio transcoding or ISO9660 image creation. I don't know if this means anything because my cdrom drive does not have burning capabilities.

My cdrom drive worked well (abeit very slowly and loudly) with edgy, and stopped being detected when I upgraded to feisty herd 5.

---

### Post by chakkaradeep on 2007-04-21
> **theWrkncacnter said:**
> I couldn't find anything in Hardware Information, and K3b couldn't either
 I don't know if this means anything because my cdrom drive does not have burning capabilities.

My cdrom drive worked well (abeit very slowly and loudly) with edgy, and stopped being detected when I upgraded to feisty herd 5.

Ok, K3B is correct as there is no CD/DVD writer as you have told you only have cd reader. 

Let us go somewhat wild now :) .Can you please paste the output of ** sudo ls /dev/s***

---

### Post by theWrkncacnter on 2007-04-21
> **chakkaradeep said:**
> Ok, K3B is correct as there is no CD/DVD writer as you have told you only have cd reader. 

Let us go somewhat wild now :) .Can you please paste the output of ** sudo ls /dev/s***
```
$  sudo ls /dev/s*
Password:
/dev/sda   /dev/sda3       /dev/sequencer2  /dev/snapshot  /dev/stdin
/dev/sda1  /dev/sdb        /dev/sg0         /dev/sndstat   /dev/stdout
/dev/sda2  /dev/sequencer  /dev/sg1         /dev/stderr

/dev/shm:

/dev/snd:
controlC0  midiC0D0  pcmC0D0c  pcmC0D0p  pcmC0D1p  seq  timer
```
I think it might be /dev/sdb

---

### Post by chakkaradeep on 2007-04-21
> **theWrkncacnter said:**
> 
I think it might be /dev/sdb

why dont you try it :)

---

### Post by theWrkncacnter on 2007-04-21
Are any of these cdrom drives?
```
~$ sudo lshw -class disk  
   *-disk:0                
       description: SCSI Disk
       product: IBM-DTLA-307030
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: TX4G
       serial: YKDYKTJG487
       size: 28GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: HPFS/NTFS partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 13GB
          capabilities: primary bootable
     *-volume:1
          description: Linux filesystem partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          capacity: 14GB
          capabilities: primary
     *-volume:2
          description: Linux swap / Solaris partition
          physical id: 3
          bus info: scsi@0:0.0.0,3
          logical name: /dev/sda3
          capacity: 674MB
          capabilities: primary nofs
  *-disk:1
       description: SCSI Disk
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       configuration: ansiversion=5
```

---

### Post by chakkaradeep on 2007-04-21
Here is my entries for cdrom,

> 
 *-cdrom
       description: DVD reader
       product: CDRW/DVD CDD5263
       vendor: PHILIPS
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: UH89
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom


Try /dev/sdb

---

### Post by theWrkncacnter on 2007-04-21
> **chakkaradeep said:**
> why dont you try it :)

This is what happens:```
$ sudo mount /dev/sdb
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

phix@patrickishere:~$ dmesg | tail
...
[ 2046.888657] UDF-fs: No partition found (1)
[ 2046.890093] isofs_fill_super: bread failed, dev=sdb, iso_blknum=16, block=32

```

---

### Post by chakkaradeep on 2007-04-21
Its really strange ! :( 

I really doubt Feisty detected your cd rom ! :(

---

### Post by theWrkncacnter on 2007-04-21
Is there anything I can do about it? I have the feisty release live cd/

---

### Post by chakkaradeep on 2007-04-21
> **theWrkncacnter said:**
> Is there anything I can do about it? I have the feisty release live cd/

Is the live cd loading ? If yes, your cdrom is working right ? Then you can identify what is your cdrom device :)

---

### Post by solderhead on 2007-04-21
thanks everyone for the help.  i'll quote a couple of references to bring us back to the place i was in troubleshooting:

> **solderhead said:**
> although it appears that i have correctly edited the entries in /etc/fstab, it appears that there are no scd* nodes in the /dev directory.

> **chakkaradeep said:**
> Can you check by typing **sudo ls /dev/scd (tab key)** so that it displays some of the devices available and you could get to know if scd0 and scd1 exists. If you find them, please do,
**sudo mount /dev/scd(x) /media/cdrom** to check whether you can mount any dvd/cd drive.

my statement about the absence of suitable nodes in /dev was an observation that i had already made.  i'm sorry, i should have been clearer about that.  at any rate, it appears that the upgrade method from Edgy to Feisty *eliminates* the required the required device driver nodes. 

just to verify that the nodes are absent, this command is the functional equivalent of the inspection method previously recommended:

```
root@todland:/dev/.udev/names# vdir /dev/sc*
vdir: /dev/sc*: No such file or directory
```

as a matter of coincidence, i was led to discover this problem when K3B reported that I have no optical drives available, even though my Lite-On CDRW worked fine with Edgy immediately prior to the upgrade.  Before I realized the nature of the problem, I opened a thread on the K3B problem:

[http://ubuntuforums.org/showthread.php?t=416086](http://ubuntuforums.org/showthread.php?t=416086)

regarding editing the entries in **/etc/mtab**, there aren't any entries in the file on my box for cd drives.  as i understand the file, mtab is created by the system after polling the available devices -- but i could be wrong about that.  at any rate, i'm thinking that the absense of any relevant entries in mtab lends a little support to my hypothesis that the problem is due to a bug/failure in device installation during the update cycle, and not due to a mistake in end user re-configuration.  just to be sure that i haven't made a configuration error that could be corrected by a suitable mtab entry, can someone tell me what line i should be seeing in mtab?  i'm more than willing to create a suitable manual entry if someone thinks its worth trying.

thanks again to everyone for their help.

---

### Post by solderhead on 2007-04-21
> **chakkaradeep said:**
> Is the live cd loading ? If yes, your cdrom is working right ? Then you can identify what is your cdrom device :)

in my case the PC would boot from the same CD drive, and the CDRW was 100% operational under every OS except Fesity -- including Edgy immediately prior to the upgrade.  This is obviously a software issue.

---

### Post by solderhead on 2007-04-21
SOLVED!

In my case, this turned out to be a kernel / udev / device recognition problem.  I'll post my solution just in case anyone else finds it helpful:

1.  Edit /etc/fstab entries as referenced earlier in this thread.  for example, my CDRW drive required the following entry.  

```
/dev/scd1 /media/cdrom0 iso9660 user,noauto 0 0
```
No editing of /etc/mtab was necessary, as proper mtab entries are supposed to be created dynamically.  note that at this point the *scdX* device nodes don't yet exist in /dev.

2.  Attempt a superuser forced mount:

```
sudo mount -a
```

the "mount" was successful in that I noticed the elimination of the error message that i had mentioned previously -- that is significant -- even though the device still failed to actually mount.  as it turns out, this is actually a good sign.

3.  Reboot the Kernel.  Although you might not think this would be necessary, it allows the kernel / udev to examine the corrected /etc/fstab file and to subsequently implement the creation of the appropriate device nodes required for the CDRW drive.  after rebooting:

a.  the device nodes appeared as /dev/scd0.
b.  suitable entries appeared in /etc/mtab:

```
/dev/scd0 /media/Kubuntu\0407.04\040i386 iso9660 ro,noexec,nosuid,nodev,noatime,uid=1000,utf8 0 0


```
I had thought about the need to reboot last night, but i had put off doing it as i was in the middle of a bittorrent download of the Feisty DVD.

I hope this helps others who are having similar problems.

---

### Post by theWrkncacnter on 2007-04-22
> Is the live cd loading ? If yes, your cdrom is working right ? Then you can identify what is your cdrom device If the live cd works, how does that help me get it working without the live cd? (I don't want to sound rude, I'm just completely clueless)

In the meantime I'm trying solderhead's solution.

---

### Post by theWrkncacnter on 2007-04-22
OK - The edgy live cd loads, but the feisty live cd gets stuck at initrafs, like solderhead said, a software problem.

When I tried solderhead's solution, mount -a returned no errors, finally, but even after I rebooted the computer, the drive ignores every disc I put into it. I don't know what to do.

---

### Post by chakkaradeep on 2007-04-22
> **theWrkncacnter said:**
> If the live cd works, how does that help me get it working without the live cd? (I don't want to sound rude, I'm just completely clueless)



If the live cd loads, it means that the cd rom is mounted and by issuing the **mount** command in the terminal (just the mount command) you can find what are mounted and deduce the cd device.

---

### Post by theWrkncacnter on 2007-04-22
When I boot into feisty with any cd in the drive (booting from the live cd or from hard disk), it starts normally, but then it slows down trying to detect the cd drive (/dev/sdb it says a lot)
I get lots of messages like "ata2: port is responding slowly; please be patient" and some I/O errors, a bunch of stuff that stops as soon as I press eject. THis doesn't happen in previous versions of ubuntu.

---

### Post by autocrosser on 2007-04-22
Take a look at the closed Feisty Development forum. I remember that some CD units do not take kindly to being addressed as SATA units. I do not believe that there was a answer to this problem (I hope I'm wrong). In any case, I'd also goto Launchpad to look for bugs about this.

---

### Post by frodon on 2007-04-22
I believe this has been solved before the release, i did the update yesterday and didn't get any problems with my dvd drives.
But if there's still some bugs please report them using launchpad it helps a lot devs to solve issues.

---

### Post by solderhead on 2007-04-22
pardon my ignorance -- what is launchpad?

---

### Post by Rui Pais on 2007-04-22
> **solderhead said:**
> pardon my ignorance -- what is launchpad?

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by nubutu on 2007-04-23
Hi

Since I upgraded to Feisty I can't use hdparm as it complains like:

sudo hdparm -d1 /dev/sda

/dev/sda:

setting using_dma to 1 (on)
HDIO_SET_DMA failed: Inappropriate ioctl for device

sudo hdparm -M /dev/sda

/dev/sda:
HDIO_GET_ACOUSTIC failed: Inappropriate ioctl for device

Whereas previously, with the /dev/hdx scheme, everything was OK. How am I supposed to address the drives to make things work?

Thanks

---

### Post by solderhead on 2007-04-23
thanks about launchpad.

hdparm is for PATA drives.  for SATA drives/drivers, i think the tool is sdparm.

---

### Post by gspr on 2007-04-23
> **psyke83 said:**
> There's two issues here:

1. Drives are using the new libata subsystem, meaning that IDE devices appear as SCSI. This is normal, and all your drives should still be working.

Should I find it strange that this is true on my laptop (hda turned into sda), while on my desktop computer, hda stayed hda and hdb stayed hdb? The desktop computer has an nForce2 IDE controller alongside a SiI 3112 SATA controller. The drives that still show up as hdX are ordinary IDE drives, and the SATA controller is UNUSED.

---

### Post by Nimefurahi on 2007-04-23
Here is yet another approach:

If the new kernel with it's libata module insists on identifying all drives by UUID numbers and having them appear as scsi devices, just let it be.

Let /etc/fstab list your drives as the live CD found them in the manner of ...

```

# /dev/hda1
_UUID=25c1fbc7-f8e2-4744-89f5-080bb9fc6261 /media/hda1 ext3 defaults,rw,user 0 2_
# /dev/hda2
UUID=87fc5b54-d8fb-4c2d-bba8-dcec0cd8c195 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda3
UUID=2f4574ca-83f4-405b-a01c-f8c79da64004 none swap sw 0 0
# /dev/hdb1[U]
UUID=2c6f7feb-63ca-449e-b77a-b02982b98dc1 /media/hdb1 ext3 defaults,rw,user 0 2[/U]

```

and let your /boot/grub/device.map remain untouched, such as ...

```
(hd0)	/dev/hda
(hd1)	/dev/hdb

```

but let's tackle /boot/grub/menu.lst. Here's mine in part ...

```
title Fiesty Ubuntu, kernel 2.6.20-15-generic (Hda2)
           root (hd0,1)
           kernel /boot/vmlinuz-2.6.20-15-generic
           root=UUID=87fc5b54-d8fb-4c2d-bba8-dcec0cd8c195
           /dev/hda1=UUID=25c1fbc7-f8e2-4744-89f5-080bb9fc6261
           /dev/hdb1=UUID=2c6f7feb-63ca-449e-b77a-b02982b98dc1
           ro splash vga=792
           initrd /boot/initrd.img-2.6.20-15-generic
           savedefault
           boot

```

Notice how grub identifies the root directory by it's UUID. That works well for the root partition and grub seems to be happy. But let's not stop there.  Let's provide grub with addition information about other drives/partitions by pointing their earlier naming convention ( i.e. hda1, hdb1, etc...) to their newly assigned UUID numbers, such as ....

```

/dev/hda1=UUID=25c1fbc7-f8e2-4744-89f5-080bb9fc6261
/dev/hdb1=UUID=2c6f7feb-63ca-449e-b77a-b02982b98dc1

```

(by the way, all of this remains as one line on the "kernel" line. I just added the carriage returns to facilitate reading.)

Following this alternative workaround will solve issues with fsck in the booting process, enable you to fdisk /dev/hdx, and present your volumes on the Gnome desktop as you're used to seeing, i.e. hda2, hda3, hdb1, etc.

In short, let kernel do want kernel wants to do. Just give it a bit more information at pre-boot. through grub's kernel line.

---

### Post by justynbutler on 2007-04-25
Any confirmation that the above menu.lst hack fixes anything? I'm trying to sort out my sister's PC remotely (I live far away)  and every time I try something and it doesn't work, she gets more annoyed.

cheers,
Justyn

---

### Post by jerrylamos on 2007-04-25
This is a four boot system - Win98, Ubuntu Dapper, Xubuntu Feisty, Ubuntu Feisty.  Grub uses the menu.lst is in whichever one of the Linux's that was installed last.

With different Ubuntu's the menu.lst is a holy mess.  Used to be I could just boot hda1 or hda2 or hdb1 or hdb3.  Now with all those UUID's flying around with this kernel or that one and this recovery or that one and this mem test or that one and this back level or that one I can hardly read the screen which goes on to several pages.

Solution every time I install (I test versions and bug workarounds :confused: and try out different Linux's) I go into the last menu.lst and edit it to put the top 4 lines the "real" ones.  I may not get it right the first time.

I can put up with this, but I'm not so sure what the "ordinary desktop computer user" sees.

Cheers, Jerry

---

### Post by Luis McDOugall on 2007-04-28
I may missed the information.
But can someone in plain English  can tell what happened with the devices hdx.

I am so stupid (or trusted ubutun developers to much) that did not notice the change from 
hd to sd and lost bunch of data. (where is my backup:confused: ):-({|= .

Anyway, I need this information to see how I fix my grub since is not locating 
the device at boot time.

thank you
guys 
-L

---

### Post by Nimefurahi on 2007-04-28
Before you make any file edits, when you boot your system, does Grub display a menu?

If Grub does display a menu, are there any available kernel selections other than 2.6.20-15-generic?

If you are lucky enough to have a line with 2.6.17-10-generic, select that one first and try to boot.

In the absence of 2.6.17-10-generic, look for 2.6.17-11-generic and try that one.

---

### Post by chalewa on 2007-04-30
> **nubutu said:**
> Hi

Since I upgraded to Feisty I can't use hdparm as it complains like:

sudo hdparm -d1 /dev/sda

/dev/sda:

setting using_dma to 1 (on)
HDIO_SET_DMA failed: Inappropriate ioctl for device

sudo hdparm -M /dev/sda

/dev/sda:
HDIO_GET_ACOUSTIC failed: Inappropriate ioctl for device

Whereas previously, with the /dev/hdx scheme, everything was OK. How am I supposed to address the drives to make things work?

Thanks


having the same problems with my disc drives....just took me 5 minutes to burn an 800 meg dvd...


why would the ubuntu team change this in the feisty release?

---

### Post by MxGB on 2007-05-10
Hello,

The change from hd* to sd* has caused me big problems. I use a few utils with my laptop to eject IDE devices and hotswap my docking station. Now the app I use (khotswap) doesn't know where to find IDE devices and I can't eject/stop any of my drives! I'm having to reboot, it's like using a desktop...

Does anyone have any knowledge of khotswap to 'bodge' a solution, or is there a way to force the kernel into naming IDE devices properly? Apologies if this has already been asked, I have been forum searching for days without joy.

---

### Post by derekguy on 2007-05-12
Many thanks for all of your posts in this thread I was unaware of the changes from hd(x) to sd(x) and was having issues with my fstab.

I have fixed them now and I can say fstab looks great cheers for all of your help.

I also have the same problem mentioned two post up I cannot set DMA to on or off and using the same command with sdparm just gives me the --help output and tells me it is an invalid command.

---

### Post by MxGB on 2007-05-29
It looks like with a recent kernel update that the old behaviour has been restored. Once I rebooted with 2.6.20-16-generic my devices were back to hdx, and after another fstab change it seems to work again.

---

### Post by MxGB on 2007-06-09
What the hell is going on? My machine has just applied an update and now my IDE drives are being called SCSI devices. Again! This is pretty annoying having to update my various apps with each update, not to mention that my system didn't boot until I changed fstab in single user mode.

Why have they done away with /dev/hd* devices? A few of the apps I use are broken again because they can't see my IDE drives and partitions. Why even bother messing with IDE device drivers anyway seing as they'll probably be obsolete in a few years time.

---

### Post by theWrkncacnter on 2007-06-10
My feisty live cd still won't start up and neither will the gutsy tribe1 disc I downloaded. The edgy disc still works.

Is this the kind of thing that I have to somehow fix, or is it a job for the devs?

--Patrick

---

### Post by armalite on 2007-06-11
> **MxGB said:**
> Hello,

The change from hd* to sd* has caused me big problems. I use a few utils with my laptop to eject IDE devices and hotswap my docking station. Now the app I use (khotswap) doesn't know where to find IDE devices and I can't eject/stop any of my drives! I'm having to reboot, it's like using a desktop...

Does anyone have any knowledge of khotswap to 'bodge' a solution, or is there a way to force the kernel into naming IDE devices properly? Apologies if this has already been asked, I have been forum searching for days without joy.

MxGB, you can try this command before ejecting the drive (being root):

```
echo 1 >  /sys/class/scsi_disk/(your_ide_drive)/device/delete 
```

your_ide_drive should be something like 0:0:0:1 or 0:1:0:0 or similar (i'm not on my notebook so i can't tell you exactly which is my cdrom drive). There should be two of these folders on a standard notebook, the first one is first drive, the second one should be the cdrom bay. Your mileage may vary.

When you have to reinsert your ide drive or cdrom (root user), after the physical drive insertion:

```
echo 0 0 0 >  /sys/class/scsi_host/host1/scan
```

This will rescan the bus drive and will let recognize the ide drive or cdrom. This is the command i use on my notebook. On my Lifebook, i have no problems in ejecting the cdrom without issuing the first command, so i only use the second one to rescan the ide bus when i reinsert the drive.

Anyway, if some of you have problems in fstab not recognizing drives, maybe it is better to use UUID, they will survive to any name change your drives will have in the future.

---

### Post by kevmacmills on 2007-06-11
FWIW:  this really, really screws up VMware virtual machines created with physical disks!!  :-|

---

### Post by MxGB on 2007-06-12
> **kevmacmills said:**
> FWIW:  this really, really screws up VMware virtual machines created with physical disks!!  :-|
Yep, am having the same problem myself.

---

### Post by MxGB on 2007-07-04
By the way, thank you armalite for your suggestions - they worked a charm. Now, to automate or GUIfy this task somehow :p

---

### Post by armalite on 2007-07-04
> **MxGB said:**
> Now, to automate or GUIfy this task somehow :p

I tried some months ago to modify the gnome-hotswap-applet (which i debianized way long ago, downloaded from hotswap homepage) to let it rescan. Anyway I never programmed python, and there where some problems in issuing commands because one must be super user to use the echo commands (well, because of file permissions, to be correct) and i have no clue on how to manage this, so my program isn't working.

Maybe restarting from scratch could be easy to create a gnome applet (kde should be similar), but the real thing i would like to see should be an automated way to issue the rescan command. If linux could see that a drive is being inserted, it could call the correct rescan and the drive should appear without user intervention. Windows already manages this, so no hardware modification is involved. I see nothing useful in logs, maybe acpi could be telling something but i tried to run acpi_event and found nothing. Module acpi_asus could be the solution but doesn't load in my Fujitsu-Siemens. 

Suggestions are welcome, as usual.

---

