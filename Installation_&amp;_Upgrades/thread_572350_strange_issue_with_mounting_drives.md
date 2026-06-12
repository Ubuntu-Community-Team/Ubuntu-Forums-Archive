---
title: "strange issue with mounting drives"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by kamasabi on 2007-10-10
I was wondering if anyone else had this problem.  I have my older computer set up as a file server, and I have 3 hard drives added that are ntfs.  Now the strange part is, every time my computer powers off / restarts, the mount names change.  For instance, say i make a drive /dev/sda1.  After I restart, it will change to something else, like /dev/sdc1.  Its rather irritating, because if we have a storm and hte power goes out, I have to go reset everything up, not to mention I have certain drives with access control, and one drive that only I am supposed to access is mixed up with one that everyone can access, so everyone gets access to my private stuff and no one gets access to the public stuff -_-.   I used the manual here to set it up:

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

I see there is a newer post on support:

[http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)

My question is, isthere a quick fix for the first method that I used?  If not, is there something different in the second one that would fix this? Does this have anything to do with the fact that they are in ntfs?  if so and there is no fix, do you think just making these fat drives would fix the issue?

<-- nub, so if you need more info let me know and I'll do my best to get ya the info you need.

Thanks!!!

Kama

---

### Post by dabl on 2007-10-10
> **kamasabi said:**
> I have 3 hard drives added 

Need more data -- you have 2 IDE channels full of drives? -- you added a SCSI card and hung them on it?  You put a USB breakout box and hung them on that? -- I think this is probably the key to answering your question.


> 
Does this have anything to do with the fact that they are in ntfs?  No.


Probably you're going to want to "mount by UUID", rather than by /dev/sd# device, since that is changing between boots.  I'm assuming the UUID numbers will be static, per partition.

For fun, open a console and enter ```
blkid
``` and observe carefully/record the output.  Then shut down and reboot and do it again.  Compare the UUIDs.  Hopefully the UUID numbers remain unchanged, although the /dev/sd# IDs might have moved between boots.

:)

---

### Post by kamasabi on 2007-10-10
right now I have a total of 6 IDE drives, 2 dvd drives and 4 hard drives.  the two cd drives and the boot drive are connected to the motherboard directly, and the other three drives are hooked up through a PCI IDE controller card.  the three hard drives on the controller card are all in NTFS, were taken out of enclosures from a windows machine and thats why I thought that might be the reason.  Right now I'm not currently at the house so I can't run that "blkid" command at the moment, but I'll update as soon as I do.  Could you explain how to mount by UUID, or point me in the direction of a "how to"?  I'm still pretty new to linux here, so all help would be greatly appreaciated!!!!

Thanks

EDIT:  ran blkid, and for for sda1, sdc1, and sdd1, it says TYPE="ntfs" , no UUID.

The other 2, sdb1 and sdb5 have a UUID with a long string of characters.  
For sdb1, after the string it says SEC_TYPE="ext2" TYPE="ext3"
For sdb5, after the string it says TYPE="swap"

---

### Post by dabl on 2007-10-10
> **kamasabi said:**
> 
the other three drives are hooked up through a PCI IDE controller card.  Do these 3 show up in BIOS at all, or just the PCI card?

> 
EDIT:  ran blkid, and for for sda1, sdc1, and sdd1, it says TYPE="ntfs" , no UUID. 

"No UUID" is a bad thing -- that suggests Linux isn't really seeing those drives at all.  I read the other day about a command to tell the OS to assign new UUIDs -- let me see if Google will help.

YES, if you have the package e2fsprogs installed, then ```
sudo uuidgen -r
``` should generate a uuid for the current drive/partition.  I guess you would need to cd to /dev/sda1 and run the command there.  Try it -- if it fails to generate a UUID, then I think you've got a real problem getting those drives to mount correctly.

Here's the general approach to setting your fstab lines to mount by UUID:

[http://ubuntuforums.org/showthread.php?p=3487407#post3487407](http://ubuntuforums.org/showthread.php?p=3487407#post3487407)

HTH!  :)

---

### Post by kamasabi on 2007-10-11
aye, all 6 drives, the 2 dvd drives and 4 hdd's all show up in BIOS without a problem.

But, on a positive note, I did a little tampering and investigation of my own, and found this link about using fstab.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Now here are my results from the listings by uuid and label.

**BY UUID**

root@VPRFIleServer:~# ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root 140 2007-10-09 15:04 .
drwxr-xr-x 6 root root 120 2007-10-09 15:04 ..
lrwxrwxrwx 1 root root  10 2007-10-09 15:04 **01C61324B4310660** -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-10-09 15:04 1295ab8d-8ecc-4548-a03b-00abcfe49b6a -> ../../sdb5
lrwxrwxrwx 1 root root  10 2007-10-09 15:04 96155227-bf44-48c8-a705-6626fb05a2d6 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2007-10-09 15:04 **BACC698ACC69422D** -> ../../sdd1
lrwxrwxrwx 1 root root  10 2007-10-09 15:04 **F06C3EB06C3E7208** -> ../../sdc1

Although they don't seem to be in the same hex format as the other 2 mounting points sdb5 and sdb1, would those other 3 still be considered UUID's?

**BY LABEL**

root@VPRFIleServer:~# ls /dev/disk/by-label -alh
total 0
drwxr-xr-x 2 root root 100 2007-10-09 15:04 .
drwxr-xr-x 6 root root 120 2007-10-09 15:04 ..
lrwxrwxrwx 1 root root  10 2007-10-09 15:04 DSK1_VOL1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-10-09 15:04 Ultra -> ../../sdc1
lrwxrwxrwx 1 root root  10 2007-10-09 15:04 Vantec -> ../../sdd1

I think this might work, but would like confirmation before I try it :p.  first create a new directories with:

mkdir /mnt/DSK1_VOL1
mkdir /mnt/Ultra
mkdir /mnt/Vantec

Then in fstab make the enties:

LABEL=DSK1_VOL1 /mnt/DSK1_VOL1 	ntfs-3g   defaults,locale=en_US.utf8   0    0
LABEL=ULTRA	/mnt/Ultra	ntfs-3g   defaults,locale=en_US.utf8   0    0
LABEL=VANTEC	/mnt/Vantec	ntfs-3g   defaults,locale=en_US.utf8   0    0

Then umount all 3 mounting points, and then remount?

---

### Post by dabl on 2007-10-11
> **kamasabi said:**
> 
Although they don't seem to be in the same hex format as the other 2 mounting points sdb5 and sdb1, would those other 3 still be considered UUID's? 

Hey, this is progress!  YES, those are valid UUIDs for NTFS-formatted partitions.

> 
I think this might work, but would like confirmation before I try it :p.  first create a new directories with:

mkdir /mnt/DSK1_VOL1
mkdir /mnt/Ultra
mkdir /mnt/Vantec

Then in fstab make the enties:

LABEL=DSK1_VOL1 /mnt/DSK1_VOL1 	ntfs-3g   defaults,locale=en_US.utf8   0    0
LABEL=ULTRA	/mnt/Ultra	ntfs-3g   defaults,locale=en_US.utf8   0    0
LABEL=VANTEC	/mnt/Vantec	ntfs-3g   defaults,locale=en_US.utf8   0    0

Then umount all 3 mounting points, and then remount?

YES, this will work to "mount by label".  FYI, in the *buntu family of Linux, non-standard hard drive partitions are customarily mounted in /media rather than /mnt, for some reason.  But it doesn't matter for any practical purpose that I know of -- your proposal will work.

The alternative would be to "mount by UUID".  In that case, your "LABEL=DSK1_VOL1" would instead be "UUID=01C61324B4310660", and the rest of that line would be the same.

:guitar:

---

