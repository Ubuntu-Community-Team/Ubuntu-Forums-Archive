---
title: "When updating, 'not enough disk space'"
date: 2015-12-17
forum: Installation &amp; Upgrades
---

### Post by steve169 on 2015-12-17
I'm running Lubuntu 15.10 on a live thumb drive (USB 3.0) that has 64 GiB of memory. I use it only for online financial transactions and sometimes playing games while I wait.

When I installed Lubuntu, I chose to encrypt it.

I update whenever I get a notice that updates are available. I install only the security updates.

This last time, I got this error message:
[INDENT]**Not Enough free disk space**
The upgrade needs a total of 94.0 M free space on disk '/boot'. Please free an additional 7,963 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
[/INDENT]

I emptied my trash (there was very little) and ran **sudo apt-get clean** twice. But still the error message appears when I try to update.

I'm something of a newbie and this puzzles me, because I have such a large capacity on this thumb drive — 64 GiB.

Gparted shows this:

[TABLE="width: 600, align: center"]
[TR]
[TD][B]Partition
[/B][/TD]
[TD][B]File Sys
[/B][/TD]
[TD][B]Mount Pt.
[/B][/TD]
[TD][B]Size
[/B][/TD]
[TD][B]Used
[/B][/TD]
[TD][B]Flags
[/B][/TD]
[/TR]
[TR]
[TD]/dev/sdc1[/TD]
[TD]ext2[/TD]
[TD]/boot[/TD]
[TD]243 MiB[/TD]
[TD]94.16 MiB[/TD]
[TD]boot[/TD]
[/TR]
[TR]
[TD]/dev/sdc2[/TD]
[TD]extended[/TD]
[TD][/TD]
[TD]58.37 GiB[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sdc5 (!)[/TD]
[TD]crypt-luks[/TD]
[TD][/TD]
[TD]58.37 GiB[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]


Have I set it up wrong?

Should I shrink the extended partition and expand the boot partition?

---

### Post by hello5 on 2015-12-17
I have the exact same issue currently, any suggestions?

---

### Post by Bashing-om on 2015-12-17
steve169; Hello,

No 'you' have done nothing wrong:
LVM /boot partition is created too small to start with.
See:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

What "might" prove effective is:
```

sudo apt-get autoremove

```
to remove any old kernels and free up disk space . ( No, the system will not initially and by default make that decision for you, it has no way to know if you want to keep/use/re-purpose old kernels )

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by steve169 on 2015-12-19
Dear Bashing-om,

The the boot partition is too small how about I enlarge it. To what size do you suggest?

---

### Post by C.S.Cameron on 2015-12-19
A Live Persistent thumb drive file system is FAT32.
The persistence file, (casper-rw) is therefor limited to 4GB.
Doing updates quickly fills the persistence file.

There are several solutions.

The first and easiest solution is to not do updates.
Do you really need the latest updates just to do banking?
(My wife has gone years between updates).

Another solution is to use a casper-rw partition instead of the casper-rw file.
The casper-rw partition can be ext2, ext3 or ext4 file system.
These are not limited to 4GB.
Let me know if you need instructions for doing this.

Yet another solution is to do a Full install to the flash drive.
This is like doing an install to an internal drive.
You can thus encrypt the home folder, etc, not a bad idea with a drive used for banking.
Let me know if you need instructions for doing this.
The main thing is to unplug your internal drive before proceeding.

---

### Post by C.S.Cameron on 2015-12-19
Oops, I see that you have already done a Full install.
I generally make the second partition mount point "/".
I then make a third partition with mount point "/home".
I also include swap space but this is optional.
You only need about 10GB for "/" giving the majority of space to "/home".

---

### Post by Bashing-om on 2015-12-19
steve169; Hey ..

> **steve169 said:**
> Dear Bashing-om,

The the boot partition is too small how about I enlarge it. To what size do you suggest?

See the above posts, all good info . We are all here to help in what ever you decide is in your best interest.
While with some difficulties and effort ..... that ^ can be done. Perhaps a better thing is to tighten up on the house keeping. All that is required is that before installing a new kernel, that older kernels are 1st removed .
When the package manager is in a consistent state the terminal commands:
```

df -h # to show the disk space usage ##
sudo apt-get autoremove

```
will perform that function. As easy as that ..

Presently, what results when running the 'autoremove' command ?

[INDENT][INDENT]the terminal is your friend
[/INDENT][/INDENT]

---

### Post by steve169 on 2015-12-19
Dear Bashing and C.S.,

The **autoremove** command worked fine, and I have updated. (I added only security updates.)

On behalf of all newbies, bless you.

My Lubuntu installation is encrypted. I would like to optimize the size of the partitions.

I tried using **Gparted**, but it would not let me change the size of the larger partition. (See chart in original message.)

Questions:

1.  Is there a way to shrink the larger partition, then expand the smaller to the recommended 10 GiB?

2.  Must I install Lubuntu from scratch to optimize these partition sizes?

---

### Post by C.S.Cameron on 2015-12-20
You can not shrink, expand or modify a partition while it is mounted and in use.
You can boot from a Live DVD or second Live USB and then modify the partitions on the first USB using gparted.

---

### Post by Topsiho on 2015-12-20
According to steve169 autoremove worked fine, but my experience using Lubuntu [COLOR="#008000"]14.04[/COLOR] is different: in that version of Lubuntu autoremove doesn't remove old and unused linux image and headerfiles, which is a nuisance. Have to do that manually. Maybe this has been improved in the newer Lubuntu 15.04.
But this improvement doesn't apply for those that use Lubuntu 14.04.

A separate /boot partition is, I think, not necessary, and therefore, not advisable.

Topsiho

---

### Post by C.S.Cameron on 2015-12-20
I have not found much use for a boot partition on a Full install USB drive myself.
I prefer to make the first partition either FAT32 of NTFS, (If larger than 4GB)
That way I can also use the flash drive for data transfer to/from a Windows PC.
(Windows can only see the first partition on a flash drive).

---

### Post by oldfred on 2015-12-21
If you do full drive encryption, you have to have the separate /boot partition.
And then you have LVM which is logical partitions over the physical partitions. The logical partitions take up all the space in the physical partitions, so you cannot easily change them.
And you have to use LVM tools to change the sizes of the logical partitions.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

