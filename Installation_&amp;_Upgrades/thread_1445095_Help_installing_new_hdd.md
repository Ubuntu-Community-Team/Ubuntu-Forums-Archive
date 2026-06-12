---
title: "Help installing new hdd"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by me13221 on 2010-04-02
Hi,

I'm upgrading from a 250GB drive to a 500GB drive.  I booted into the live-CD, ran gparted and created the necessary partitions:
/dev/sda1 ext4 /
/dev/sda2 swap
/dev/sda3 ext4 /home

then I used dd to transfer data from the old drive to the new drive.

Now I am unable to boot into the new drive.  I tried to boot again from the live-CD but fdisk reports that the drive has no partition table.  I can still mount the devices (e.g. mount /dev/sda3 /mnt/sda3) and I can see all the files.  But without a partition table, I can't set one partition to be bootable.

Why doesn't gparted create a partition table?  it created the filesystems just fine.

how do I boot into the new disk?

What do I have to do to make grub handle the new disk?

thanks in advance.

---

### Post by SoloSalsa on 2010-04-02
Instead of using dd for each individual partition, use it to duplicate the entire disk.  Since you will be moving to a larger disk, you will have a lot of unallocated space, but there will be no data loss problem (or really anything else).

For instance, if you original 250GB disk is sda, and the new 500GB disk is sdc:
```
dd if=/dev/sda of=/dev/sdc
```
When you duplicate the entire drive, the partition table, boot record, data, **everything** gets included.  When you duplicate each partition separately, the boot record and partition table can be left out.  You can then expand the last partition to fill the rest of the disk, or you can set-up additional partitions in that space.

---

### Post by me13221 on 2010-04-02
Thanks!  As usual, I was making everything far too complicated.

One other question-- now that ubuntu uses UUIDs to identify disks in grub and fstab, I assume I need to mount the new drive and update the lines in fstab and in menu.lst to use the new UUID.  I'm fine with modifying fstab, but grub has always struck me as having a lot of 'secret sauce'.  Basically, I'm proposing:

```

sed -i.old 's/<old-UUID>/<new-UUID>/g' menu.lst

```

will this work?

thanks again.

---

### Post by oldfred on 2010-04-02
If you use dd I think it copies the UUIDs also if both drives are mounted grub may boot either drive. You can reset UUIDs and then edit fstab & grub.

I also saw one poster who used dd to copy to a large drive and we could not figure out how to make it see the larger size. It copies everything so it saw it as the same size (in your case the 250gb). I think he solved it only with tools from the HD mfg to reset the total sectors value. dd is for exact copies from/to the same size partitions.

---

### Post by me13221 on 2010-04-03
OK, so I used dd to duplicate the entire drive:

```

dd if=/dev/sda of=/dev/sdb bs=4096

```

After that I used gparted to resize the new partition(s).  Then I shut down and removed the old drive.

I just finished booting into the new drive without a hitch!

Some notes for posterity:

 1- yes, the dd operation copied *everything*, including partition table, boot sector, and, surprisingly, UUID.  I thought UUIDs were supposed to be "Universally Unique" ... ([wikipedia]("http://en.wikipedia.org/wiki/Uuid")) .. but it's just as well that they aren't since I didn't have to mess with grub.

 2- I found that dd ran with better performance if I used a larger block size.  I used bs=4096 (the default is 512) and got an average speed of 33.6 MB/sec for the dd operation.  The first time I did it (with the default) I got only 15.1 MB/s. 

Thanks for the input.

---

### Post by srs5694 on 2010-04-03
> **me13221 said:**
> 1- yes, the dd operation copied *everything*, including partition table, boot sector, and, surprisingly, UUID.  I thought UUIDs were supposed to be "Universally Unique" ... ([wikipedia]("http://en.wikipedia.org/wiki/Uuid")) .. but it's just as well that they aren't since I didn't have to mess with grub.

UUIDs are data, just like anything else stored on your hard disk. The dd command does a byte-for-byte copy, so your UUIDs get copied over, too. I'm sure there are utilities that will change UUIDs as they're copied, but they'd have to understand whatever data structures they're used in (partition tables, filesystems, etc.), and dd just isn't that smart -- nor should it be, given what it's supposed to do.

---

### Post by SoloSalsa on 2010-04-05
I am glad you have your new drive online.  Thank you for mentioning block size: last time I used dd with the default setting, I was only getting 10MB/s.

---

