---
title: "lost partition after upgrade to 11.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by iomo on 2011-05-01
I need help with the recovering of a whole HDD that i can't acces anymore after
the upgrade to 11.04.
In short i cant acces a HDD of 2TB that vas formated with ext4 file system and
fsck and testdisk can't resolve anything.
The long story is:
I have a 2TB SATA disk i use only for backup storage.
My fault was that i formated it trough the graphical interface (disc utility) in
ubuntu 10.10 and it was monted on demand  so i don't now how it was partitioned
(i selected whole disk when asked for) and how it was monted (fstab has no entry
for it).
The disk was represented as the SHDD7 volume in the amovible media list and on
click was monted with full access.
I received the notification of upgrade and i started it trough system update. As 
the system signaled it has low disk space (1.8 gb left) i tried to move some
files on the backup disck. I noticed that i can't move the files because the
SHDD7 was monted read only so i let it gfo like this and i had luck and the
upgrade went without problems.

I restarted the system and everyting worked fine until i tried to mount again
the shdd7 volume from the amovible media list . It complained that the
filesystem had errors and i should run fsck.
And hear it began:
the disk was identified in the disk utility as /dev/sda
I supposed that it exists only one partition and i tried to fsck /dev/sda1 but
that give me the error that /dev/sda1 don't exist

I tried then fsck /dev/sda and this worked but gave me errors in step 1 (inode
verification if i am correct). I stupidly began to say yes to the modificatrion
until i realized that they where to many errors and i should not modify anything
until i ask someone that knows better. I stopped fsck with Ctrl-C and i googled
arround.I found that most recomandation where for testdisk. So i instaled it and
run it.
testdisck identified the disk but found no partition to start with so it was
useless.

Fdisk also found no partition on the disk and complained about the partition
table not ending wirh the right signature
So i make the second bigger mistake.i assumed that only the partition table was
corupted and by restoring it i should recover my partition
So firstly i writed a new MBR with testdisck and secondly i created with fdisck
a partition over the whole disk.
This gave me no more errors in fdisk and testdisk had a partition to work on.
But nothing functioned further.
Testdisck found no superblocks or anithing to
restore.
I have tried some of the other advise found but with no results

for the /dev/sda1

sudo mke2fs -n /dev/sda1
mke2fs 1.41.14 (22-Dec-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
122101760 inodes, 488378000 blocks
24418900 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
14905 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
    102400000, 214990848

sudo fsck.ext4 -b 294912 /dev/sda1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext4: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

same results for all superblocks listed above

sudo mke2fs -n /dev/sda
mke2fs 1.41.14 (22-Dec-2010)
/dev/sda is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
122101760 inodes, 488378381 blocks
24418919 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
14905 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
    102400000, 214990848

sudo fsck.ext4 -b 294912 /dev/sda
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda contains a file system with errors, check forced.
Resize inode not valid.  Recreate<y>?

same results for all superblocks listed above. It finds the same errors it found
when i run  fsck  on /dev/sda but now i have answered with no and interrupted after first 10 errors

So it is hope to recover something? 
Beside the answer with yes to a fsck that i intrerupted and the partition table, i have not modified anything. The smart monitor indicates that the disk is phiscaly healthy.
The disk is a 
Western Digital WDC WD20EARS-00MVWB0
What should i do? What tool to use?
Thank you very much!

---

### Post by srs5694 on 2011-05-01
First, when you're attempting to recover data on a damaged hard disk, ***never, ever even think of using mkfs or its variants!!!!!!!!!*** Creating a new filesystem necessarily writes data to points on the disk that might have held your old file data, thus making it harder to recover your files. Worse, by using mke2fs *twice*, once on the raw /dev/sda device and again on a /dev/sda1 partition that you created, you've done twice the damage, since each time you wrote fresh ext2fs data structures over different parts of the disk. Essentially, what you did was like shooting a machine gun at a box that held delicate china in an effort to open the box.

That said, it's possible you'll be able to recover some files using [PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec). If I understand how it works, you'll need another disk big enough to hold any files that PhotoRec recovers. Chances are you'll lose the filenames, so you'll need to manually identify every single file.

If you've got backups, you'll find it much easier to restore them and forget about anything you created or changed after the last backup. If you don't have backups, start making them on the disk you have left over after you use PhotoRec.

---

