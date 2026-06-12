---
title: "Ubuntu Install hangs when setting up encrypted partitions"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by dodtsair on 2008-08-12
Hello I am installing a new Ubuntu Server.  I have 2 200GB sata drives.  I am trying to set them up to mirror and to be encrypted. 

At this point I use manual partitioning to set up the drives.  At the point I tell it to set up the encrypted volumes it hangs at 42% saying "Setting up the partitioner"

I can inspect the system using another console and the ls of /dev/mapper only has control in it.  So it seems it is hanging when setting up the encrypted devices.

Here is the configuration I am using
/dev/sda 200GB
/dev/sdb 200GB
Partitioned:
/dev/sda1 512MB (for boot)
/dev/sda2 8.196GB (for swap)
/dev/sda3 rest of the drive (for root)

/dev/sdb1 512MB (for boot)
/dev/sdb2 8.196GB (for swap)
/dev/sdb3 rest of the drive (for root)

I then create three software mirrors (my raid chip is fakeraid so I do not use it).
/dev/md0 (sda1 + sdb1, RAID1)
/dev/md1 (sda2 + sdb2, RAID1)
/dev/md2 (sda3 + sdb3, RAID1)

Once that is done I use md0 is an ext3 partition for /boot
I use md1 as an LVM for encryption, I set the keydepth to 128 and the passkey to random.
I use md1 as an LVM for encryption.  I set the keydepth to 128 and use a password as the encryption key.

Once I do that I tell it to set up the volumes for encryption.  It starts stuff and then eventually hangs.

While you are reading this I think  I will try using one md device and partition that into three partitions.  I am not sure if that will work.

Mike Power

---

### Post by dodtsair on 2008-08-13
Opps typo "I use md1 as an LVM for encryption. I set the keydepth to 128 and use a password as the encryption key."

md1 should be md2

---

### Post by dodtsair on 2008-08-13
One thing I learned do not try mdadm or lvm2 on Knoppix.  Knoppix seems to grab the devices for non-exclusive permissions (my guess).  Hence even when you telinit down to 1 mdadam and pvcreate fail to get and exclusive lock.  You try booting knoppix straight into run level 1, but at that point you might as well use the ubuntu install and switch to another console when it asks you for the computer's name.

Also I determined why the installer hung.  I said I was going to try and mirror sda to sdb and then split the result up into three partitions.  Well I did that except I used the installer and the installer wouldn't let me partition the raid.  I am guessing manual tools would have the same constraint.  So I switched to LVM

I put the entire raid1 device into a lv group and then created 3 lvs from that group.  Then I enabled encryption on the volumes much like I did above.  This had the side effect of sorting the lv alphanumerically (my assumption).  Hence root now comes before swap.  

When I entered my passwords and let the installer do its thing it hung at the same place.  This time I again switched to another console and noticed that ls of /dev/mapper showed the root but not the swap.

Hence I conclude this is a bug in the installer (perhaps it is using LUKS for the swap and LUKS doesn't like the random password).  When you create an encrypted swap with a random key the install hangs.

Have much other unrelated troubleshooting I determined that the installer would not hang on the same setup if a password was used.  I ran into other bugs though.

---

### Post by dodtsair on 2008-08-13
A couple oddities/bugs in the installer.  One thing to remember I am using several technologies that have been demonstrated to work on their own, but I have not seen mention of them all working in tandem.  I can understand why the installer is struggling in this area.  It ultimately failed to support my configuration due to several bugs and such, but it helped out greatly.  It would have been awesome if it had been able to setup the system.

A couple problems I ran into if I can remember them.

Once you set up RAID, LVM, or encryption the installer doesn't seem to be capable of tearing them back down.  I keep getting sharing violations on the new devices.  So whenever I made a mistake I had to reboot.

I mentioned the bug with encrypted swaps and random keys.  Well it took me a while to verify because of another bug.  The installer is nice in that it will look at your filesystem and figure out what your configuration is and begin to build it up for you.  This is awesome when you want to keep it.  In my case I wanted to make sure everything was kosher and start all the way back from sda and sdb.  But since the installer doesn't tear down things well I did it manually.

This entailed a reboot a switch to console when it asked for my new computer's name.  There I used fdisk to delete all the partitions.  Now the installer would detect empty disks.  When I continued the installer it did indeed pick up empty disks.  I partitioned them exactly the same way before but when I went to set up the RAID1 it already had one of the three raids setup, and it was sitting on device 3 not 0 like I would have expected.

At this point since I used the same exact numbers to partition I figured there was some meta data on the disk telling the OS about the RAID1.  Hence when I used the exact same partitions and the installer redetected the disk I suspected if found the meta data again and recreated the RAIDS.  Not what I wanted, reboot.

This time I switched to the console at the same time.  I used dd if=/dev/zero of=/dev/sd@# on each disk for several seconds.  I assumed that was enough time to put down several MB of zeros onto the head of each partition.  Then I deleted using fdisk all partitions.  Following that up I dumped zeros on sda and sbb the same way.

Even with this done, it still picked up the all RAID arrays.  This time I think it may have picked up 3 number 2-4.  I do not remember this part well.  So I decided maybe the meta data was at the end of the partition, but heck if I know.  Reboot, console, dd if=/dev/urandom of=/dev/sda 

One and a half days later the installer is no longer picks up the artifacts.  I verify that the installer doesn't hang when using a swap with password.  But then I ran into more bugs.

---

### Post by dodtsair on 2008-08-13
Another bug I encountered.  Set up two partitions for swap, mirror them, put an encryption volume on them with password all done using the manual partition.  When I told the partitioner to finish we should have moved on to installing the base system.  However the installer failed to turn on the swap.  I switched to another console tried to swapon the device myself (lacking man pages or web access) but it only said invalid device.  Not sure what is going on there (could easily be user error).  In any case I am starting to enter path of least resistance mode.

So I go back to the partitioner and change the swap partition to be unused.  Continue through to installing the base system.  It gives me a warning about no swap, I say yeah yeah I'll fix it once I get a base system going.

At this point is successfully installs the base but I ran into another "bug" or missing feature.

---

### Post by dodtsair on 2008-08-13
So once the installer installed the base system without a swap it offered me the chance to install LILO.  LILO?  isn't it this funky old arcane thing...?  Being still stubborn at this time I went back the the installer list of steps in order to choose install grub.  But it wasn't there, ideally I would like it to still be there (otherwise how am I to know why it isn't in order to fix it).  Just give me a warning that it always crashes when used in this configuration like it does when using xfs for /boot.

So at this point back to path of least resistance.  I know grup works with whole disk encryption and I know that grub works with software RAID1.  I just do not know that the installer can do it with both.  So reboot on to more problems.

---

### Post by dodtsair on 2008-08-13
So at this point I decided to set up Software Raid only during the install and incrementally turn on encryption later.  I have read some guides that do that.  

So reboot, same three partitions on both disks, same three RAID1s but this time instead of assigning the / partition and the swap partition to encrypted volumes.  I just use them as xfs and swap respectively.

At this point the base system installs and again I get offered the chance to install LILO.  I do not have a gripe against LILO I just know that this works with grub and I know that most systems now a days use grub and I want to to.

I choose go back.  Grub is now an option in the installer's list of tasks.  But when I choose to install grub it starts to churn on my configuration and then crashes.

Well I guess I am going to have to build this whole thing incrementally

---

### Post by dodtsair on 2008-08-13
So my next step one, I see a whole bundle of guides setting up software raid using the installer, but they do not have a /boot partition and they are not using xfs.  So I will try that once or twice to figure out which particular configuration is failing.

Then at one point I found an install the migrated an existing linux system onto a software raid using a degenerated (right word?) RAID1 on the second disk (sdb) and copying everything over from the first to the second.  I'll try that.  Then I'll attempt to use the same trick to build up an encryption filesytem.

---

### Post by dodtsair on 2008-08-14
Another bug/missing feature in the installer.

If you have two disk, say /dev/sda and /dev/sdb.  Then the installer can install when you partition them like so

sda1 ext3 /boot
sda2 swap
sda3 ext3 /

sdb1 ext3 /boot
sdb2 swap
sdb3 ext3 /

md0 RAID1 with sda1 and sdb1
md1 RAID1 with sda2 and sdb2
md2 RAID1 with sda3 and sdb3

However it will not install when you switch sda3 and sdb3 to xfs.  GRUB fails which seems broken since a major point of using a /boot partition is to allow the kernel to stand up on a fs grub knows about and then boot into (root) an fs that GRUB may not know about.

---

### Post by dodtsair on 2008-08-14
At this point I am starting to outstrip my linux abilities.

At this point I have an installed Ubuntu system on /dev/sda like so
/dev/sda1 512 MB /boot
/dev/sda2 8 GB swap
/dev/sda3 ~ GB /

I can repartition and allocate /dev/sdb any way I want I still get the same result:

mpower@dodtsair:~$ sudo mdadm --examine --scan
[sudo] password for mpower: 
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=b66843de:f5934a48:28bd14ef:bd795c43

At this point I have not set up any software raid and yet I am getting one detected on /dev/md1.  I wonder what device that UUID refers to.  Lets look at the possible candidates

mpower@dodtsair:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-08-13 23:27 b0ffcb6d-d664-436b-9274-c4e48bed851b -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-08-13 23:27 e39f7263-7153-4752-a97b-b107f19f5b4b -> ../../sda1

Odd for some strange reason that UUID doesn't seem to exist, yet mdadm is detecting it being used for md1.  

I am at a loss on how to fix this.  My last hope is to dump random data across /dev/sdb and hope that ubuntu some how forgets this non existent raid on md1.

I don't suppose I could get some help?

---

### Post by dodtsair on 2008-08-15
At this point I am hopelessly stuck.  For some reason the system thinks I have a degenerated raid1 on a UUID that I can not find on my system.  I wrote zero's across the entire /dev/sdb harddrive (dd if=/dev/zero of=/dev/hdb).  Even after rebooting mdadm --examine --scan still picks up the raid1 sitting on /dev/md1.  I have no clue how it is finding this raid that doesn't exist.  I double checked /dev/sda1 and /dev/sda3 which have ext3 and xfs filesystems on them respectively.  None of them are using this UUID.

I am left with no choice but to completely zero out both harddrives and start all over.

---

### Post by Midahed on 2009-01-29
Did you ever solve this?  None of my attempts to get RAID1, LVM and encryption working on 8.04 using the alternate install CD have worked...  If you did eventually manage to crack the problems, I'd love to know how.

---

### Post by dodtsair on 2009-10-28
Nope, I gave up on most of what I was doing.  I have a LVM system with ext3 on it.  No raid at all.

---

