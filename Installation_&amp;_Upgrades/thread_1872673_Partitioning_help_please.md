---
title: "Partitioning help please"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by Cool Javelin on 2011-10-31
I am trying to convert my file systems to ext4 on Ubuntu 8.10 text only sustem (No GParted)

Using parted:

```
(parted) mkpart primary ext4 0 100%
(parted) print
Model: ATA Maxtor 92739U6 (scsi)
Disk /dev/sda: 27.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      512B   27.4GB  27.4GB  primary  ext4

```

First question, where it says msdos, What's that about? Is it OK or do I need to do something about it?

After quitting parted, I did and get:

```
~$ sudo mke2fs -T ext4 /dev/sda1
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
1672800 inodes, 6688709 blocks
334435 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
205 block groups
32768 blocks per group, 32768 fragments per group
8160 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 39 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```

So far, so good, but the results of:

```
~$ blkid
/dev/sda1: UUID="74106219-ab42-46d7-a14a-0374aeb9faa0" TYPE="ext2"
```

Note it reports ext2.

Second, (and much more important) question, What's wrong, and how do I fix it?

Thanks, Mark.

---

### Post by dino99 on 2011-10-31
sorry i've never used parted, but your issue seems to be due of using mkpart instead of mkpartfs

[http://www.thegeekstuff.com/2011/09/parted-command-examples/](http://www.thegeekstuff.com/2011/09/parted-command-examples/)

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?chap=4&part=1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?chap=4&part=1)

---

### Post by prshah on 2011-10-31
> **Cool Javelin said:**
> I am trying to convert my file systems to ext4 on Ubuntu 8.10 text only sustem (No GParted)

Second, (and much more important) question, What's wrong, and how do I fix it?

ext4 default support is built in from 9.10 onwards. I suspect that using 8.10 is the problem. I suggest that you upgrade. EOL for 8.10 was in April 2010.

ext4 is backwards compatible with ext2 and ext3. So you won't get any errors, but you will lose the important journalling capabilities of ext4.

---

### Post by coffeecat on 2011-10-31
Just to pick this point up:

> **Cool Javelin said:**
> 
Partition Table: msdos

...

First question, where it says msdos, What's that about? Is it OK or do I need to do something about it?

You have an MBR partition table which parted refers to as an msdos partition table. That's quite OK.

---

### Post by Cool Javelin on 2011-10-31
Thanks coffeecat:
I thought it might be the MBR and I will probably leave it. It would be nice to know what tools I would use to alter it for education purposes.
----
dino99:
I did try mkpartfs and parted complained that ext4 (and ext3 too for that matter) were not recognized.

I will look into the links you suggested when my mind stops spinning from all the honeydo jobs I am doing today.
----
prshah:
So, you are suggesting 8.10 cannot create ext4, OK, I will follow for a moment.

Another note I should have added, I do have other drives on the system, (4 in all) 2 of the others are NTFS, and the third is ext3.

Because ext2 doesn't have the journalling stuff, I would assume it would be overall faster then ext3. But, I read that ext4 may be faster then either ext2 or ext3 (the reason I wanted to go with ext4)

I don't remember how I got the one drive to be ext3. Maybe Gparted (on the live CD) does support ext3. I haven't tried to boot the live CD yet to verify.

Obviously, the 2 NTFS's came from a Windows machine.
----
OK, I must be going batty. I just looked again, and parted and blkid agree that the partition is ext4.
----
prshah, thanks for pointing out the lack of support for the later systems in 8.10. I need to do more research to see if it is worth using ext3 or ext4, of if I should simply stay with ext2.
----
I guess I am good to go, so in a day or so, I will mark this as solved, but I don't know what happened. Thanks for all your help.
----
Just for something to read:

```
~$ blkid
/dev/sdb1: LABEL="LEGOLAS_40G" UUID="8824C64B24C63BC6" TYPE="ntfs"
/dev/sdc1: UUID="7049bc4e-e877-426e-81bc-37d8c5b43b93" TYPE="ext3"
/dev/sdc5: UUID="f226c457-8da7-4411-b971-18a14e161d6e" TYPE="swap"
/dev/sdd1: LABEL="LEGOLAS_80G" UUID="9C0CED510CED274C" TYPE="ntfs"
/dev/sda1: UUID="80d9c8c1-a5ec-46f1-b0da-47f2a62736cb" TYPE="ext4"

and df

~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1             13784152   1401388  11682556  11% /
none                    120288       232    120056   1% /dev
none                    124496         0    124496   0% /dev/shm
none                    124496       524    123972   1% /var/run
none                    124496         0    124496   0% /var/lock
none                    124496         0    124496   0% /lib/init/rw
none                  13784152   1401388  11682556  11% /var/lib/ureadahead/debugfs
/dev/sdb1             39086112  27764072  11322040  72% /40G
/dev/sdd1             78148160  10568628  67579532  14% /80G
/dev/sda1             26334864    176064  24821060   1% /25G

and parted

:~$ sudo parted
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA Maxtor 92739U6 (scsi)
Disk /dev/sda: 27.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      512B   27.4GB  27.4GB  primary  ext4

(parted)

```

---

