---
title: "Formating/Partitioning 3T External Drive"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by morilibus on 2011-09-02
Hello,

I just bough a 3T western digital External Hard drive:
[http://www.memoryexpress.com/Products/PID-MX31783%28ME%29.aspx](http://www.memoryexpress.com/Products/PID-MX31783%28ME%29.aspx)
I'm trying to format and partition it, but I'm not having any luck.

I tried using the disk utility, and it sort of formatted it except it shows up as only 349.31 gb of unallocated space

I tried using Gparted but it shows the same for space and then crashes anyway if I try to create partition table.

If I run** fdisk**

```
marc@Tri-Serv:/dev$ sudo fdisk /dev/sdh
Note: sector size is 4096 (not 512)
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xd8a47f91.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 45599.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

WARNING: The size of this disk is 3.0 TB (3000558944256 bytes).
DOS partition table format can not be used on drives for volumes
larger than (17592186040320 bytes) for 4096-byte sectors. Use parted(1) and GUID 
partition table format (GPT).

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

```

this shows the correct size at least, but I'm not sure how to proceed.

any tips?

---

### Post by oldfred on 2011-09-03
In gparted under device, create partition table, choose advanced and select gpt.

gpt will not work with Windows installs unless you have UEFI. Windows should be able to read data.

Also install gdisk or use gdisk from command line to create partitions.
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

For Ubuntu your will need a bios_grub partition. Create that in advance and use manual install or else grub2 will not install correctly.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by YesWeCan on 2011-09-03
Disk Utilty can also be used to create a GUID Partition Table format.
Just click "format drve" and select it.
Then create a tiny partition with no format (empty) and set its flag to bios_grub.

---

### Post by srs5694 on 2011-09-03
Much of what oldfred wrote, and YesWeCan's suggestion about how to create a BIOS Boot Partition, applies only to boot disks; but as this is an external disk that's showing up as /dev/sdh, my hunch is that you don't intend to boot from it. If you do, please elaborate. If you don't intend to boot from the disk, you needn't be concerned with GPT boot issues like a BIOS Boot Partition, UEFI support, or boot loader installation.

Also, the fdisk output indicates that the disk has 4096-byte sectors. Some external disks use such sector sizes specifically to get around the limitation of MBR (aka "msdos" and other names) partitioning, which is 2^32 sectors. With 512-byte sectors, this works out to 2 TiB, but with 4096-byte sectors, it's 16 TiB. In other words, despite the warning in fdisk, your disk *can* be used with MBR partitions. I'm guessing there's a bug in fdisk that causes it to compute the limits based on disk size in bytes rather than in number of sectors. In fact, if you check the warning, you see that it specifies the limit as 17,592,186,040,320 bytes, whereas your disk is smaller, at 3,000,558,944,256 bytes. The fact that your disk is smaller than the limit is obfuscated by the fact that the values lack commas in the fdisk output (I've added them here) and aren't directly on top of each other, making comparison of their size more difficult.

What I find troubling is the fact that you said Disk Utility reported the disk size to be 349.31 GB. You also said you tried using it to create partitions but they didn't show up. In the past, libparted (upon which Disk Utility, parted, GParted, and some other tools are based) didn't work well with disks with other-than-512-byte sector sizes. If you're using an old version of Disk Utility, it could be you're running into such a bug, which would make it unreliable on your disk. For that matter, I'm not sure when -- or even if -- these bugs were completely eliminated.

In a worst-case scenario, you should be able to use fdisk, or its cousins sfdisk or cfdisk, to partition the disk using MBR, then use mkfs to create filesystems on it. Alternatively, you could use GPT fdisk (gdisk or sgdisk) to do the partitioning with GPT, and then use mkfs to create filesystems. For a 3 TB disk with 4096-byte logical sectors, either MBR or GPT should be fine. I prefer GPT for various reasons, but if you're more comfortable with MBR, that's fine.

If you really want to avoid using command-line tools like fdisk or gdisk, I recommend you post more information:


[list]
[*]What version of Ubuntu (or other Linux distributions) are you using?
[*]What version of Disk Utility are you running? (Select Help -> About to find out.)
[*]Download the  [Boot Info  Script,](http://sourceforge.net/projects/bootinfoscript/) run it, and post the RESULTS.txt file that it produces.
[/list]


If you're running fairly old tools, you may be able to work around the problem by using an emergency disc, such as [Parted Magic](http://partedmagic.com/) or [System Rescue CD.](http://www.sysresccd.org/) These usually keep fairly up to date with software, so if you download the latest version, it may use a version of libparted that works better than what you've got.

---

### Post by morilibus on 2011-09-03
DOUBLE POST, see below.

---

### Post by morilibus on 2011-09-03
Thanks for the helps everyone,

> **srs5694 said:**
> 

If you really want to avoid using command-line tools like fdisk or gdisk, I recommend you post more information:


[LIST]
[*]What version of Ubuntu (or other Linux distributions) are you using?
[*]What version of Disk Utility are you running? (Select Help -> About to find out.)
[*]Download the  [Boot Info  Script,]("http://sourceforge.net/projects/bootinfoscript/") run it, and post the RESULTS.txt file that it produces.
[/LIST]


If you're running fairly old tools, you may be able to work around the problem by using an emergency disc, such as [Parted Magic]("http://partedmagic.com/") or [System Rescue CD.]("http://www.sysresccd.org/") These usually keep fairly up to date with software, so if you download the latest version, it may use a version of libparted that works better than what you've got.

You are correct that I have no desire to boot from this external drive, in fact it's only purpose is to back up data.


[LIST]
[*]Ubuntu 9.10  ( I plan on upgrading the whole system, **after** I'm able to back up my data.
[*]Disk Utility 2.28 Gparted 0.4.5
[*]```
boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "/usr/lib/initramfs-tools/bin/busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Computing Partition Table of /dev/sdc...
Computing Partition Table of /dev/sdd...
Computing Partition Table of /dev/sde...
Computing Partition Table of /dev/sdf...
Computing Partition Table of /dev/sdh...
Computing Partition Table of /dev/sdi...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sdb1 for information... 
Searching sdc1 for information... 
Searching sdd1 for information... 
Searching sde1 for information... 
Searching sdf1 for information... 
Searching sdi1 for information... 
Searching md0 for information... 

Finished.
```
[/LIST]
Also to clarify:

Disk Utility does shows the correct volume in the panel on the left hand side. but when I did manage to create a file system on it, it was only the 349.31GB.

Gparted only shows an unallocated  partion and filesystem of the 349.31GB

---

ok I just tried again using disk utility:

it shows two things on the right hand side when the drive is selected

[LIST]
[*]create Filesystem
[*]create Partition Table
[/LIST]
I put do not partion (create) and ext4 for the filesystem (create), and I get this error

```
Error creating file system: helper exited with exit code 1: helper failed with:
mke2fs 1.41.9 (22-Aug-2009)
```

I'm ok with doing everything in the terminal as long as I have some sort of guide with the various steps involved. 

Thanks again,

---

### Post by srs5694 on 2011-09-03
If you intend to use the disk mainly from Linux and put a Linux filesystem on it, using Windows to partition it is not something I'd recommend. Windows doesn't ship with tools to create or access Linux filesystems (although such tools are available as third-party utilities), so you'd probably end up using NTFS from Windows. This creates problems in Linux because there are no good Linux NTFS maintenance tools, so when (not if) the disk is accidentally unplugged or otherwise improperly shut down, it will become inaccessible from Linux until it's checked in Windows. This might not be too tedious for an external disk if you've got a Windows system handy, but it will be inconvenient at best and a major hassle at worst (say, if your Windows system chooses the same moment to become unbootable, as Murphy's Law says it will). There's also the fact that, as a non-native filesystem, Linux's NTFS support isn't likely to be as reliable as it is for a Linux-native filesystem.

Moving on, Ubuntu 9.10 is pretty old, and I expect that its version of libparted has the bugs I mentioned that prevent it from working reliably with your disk. Thus, you'll have to use another tool -- fdisk, gdisk, or a libparted-based tool from an emergency disc. Of these, fdisk is likely to be the easiest to get working, since it's already installed. You should be able to do the job as follows:


[list=1]
[*]Launch fdisk on the disk by typing "sudo fdisk -u /dev/sdh", changing "/dev/sdh" if your device filename has changed.
[*]Type "p" to verify that the partition table is empty. (This command should return some basic disk information and an empty partition table list.) If it's not empty, you may be working on the wrong disk, or your earlier attempts may have written something. If this is the case, you should type "q" to quit and figure out what's going on before proceeding; you do *not* want to accidentally trash one of your other disks!
[*]Type "n" to create a new partition. Tell it to create a primary partition and give it the default values, which should create one big partition to fill the disk. (Alternatively, specify a smaller partition and issue multiple "n" commands if you want to create multiple partitions.)
[*]Type "p" to view the partition table. You should see the partition(s) you created.
[*]Type "w" to save your changes. The program will exit.
[*]Type "mkfs -t xfs /dev/sdh1" (changing /dev/sdh1, if your device filename is different) to create a filesystem on the disk. Note that /dev/sdh1 is the first partition on the /dev/sdh disk. If you created multiple partitions or specified a different partition number, you may need to repeat this command or specify a different partition number. The mkfs command might take a couple of minutes to prepare a disk as big as you've got, especially if it's connected via a relatively slow USB 2 interface. You can specify a different filesystem by changing "xfs" to something else, such as "ext3" for ext3fs or "ext4" for ext4fs. I specified xfs because that works well with big multimedia files, and it sounds like you'll be backing them up to this disk. Ext3fs or ext4fs are more popular overall, but ext4fs is new enough that I'm not sure if Ubuntu 9.10's ext4fs support is fully compatible and reliable, so I'd be reluctant to use it without doing more research or upgrading the OS first.
[/list]


At this point your disk should be usable. You might see a disk icon appear on your screen, or you may need to unplug it and plug it back in again before the desktop will auto-mount it for you. If you have problems, post back with details.

---

### Post by morilibus on 2011-09-03
my raid is set up with XFS filesystem also, so that works fine with me.

I tried following your directions(which were very clear).  I went through them again to make sure i didn't make any mistakes, and the whole process was somewhat familiar as I've used fdisk before.  That being said, I got an error on step 6 when using mkfs.

here is my terminal log

```
**marc@Tri-Serv:~$ sudo fdisk -u /dev/sdh**
Note: sector size is 4096 (not 512)

The number of cylinders for this disk is set to 45599.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

WARNING: The size of this disk is 3.0 TB (3000558944256 bytes).
DOS partition table format can not be used on drives for volumes
larger than (17592186040320 bytes) for 4096-byte sectors. Use parted(1) and GUID 
partition table format (GPT).


Command (m for help): p

Disk /dev/sdh: 3000.6 GB, 3000558944256 bytes
255 heads, 63 sectors/track, 45599 cylinders, total 732558336 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63   732558335  2930233092   83  Linux

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First sector (63-732558335, default 63): 
Using default value 63
Last sector, +sectors or +size{K,M,G} (63-732558335, default 732558335): 
Using default value 732558335

Command (m for help): p

Disk /dev/sdh: 3000.6 GB, 3000558944256 bytes
255 heads, 63 sectors/track, 45599 cylinders, total 732558336 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63   732558335  2930233092   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
**marc@Tri-Serv:~$ sudo mkfs -t xfs /dev/sdh1**
mkfs.xfs: warning - cannot set blocksize on block device /dev/sdh1: Invalid argument
Warning: the data subvolume sector size 512 is less than the sector size 
reported by the device (4096).
meta-data=/dev/sdh1              isize=256    agcount=4, agsize=48921841 blks
               =                      sectsz=512   attr=2
data        =                       bsize=4096   blocks=195687361, imaxpct=25
              =                       sunit=0      swidth=0 blks
naming   =version 2          bsize=4096   ascii-ci=0
log         =internal log       bsize=4096   blocks=32768, version=2
             =                       sectsz=512   sunit=0 blks, lazy-count=0
realtime =none                extsz=4096   blocks=0, rtextents=0
mkfs.xfs: pwrite64 failed: Invalid argument
mkfs.xfs: read failed: Invalid argument

```

It looks like I need to change the sector size to 4096, however I'm not sure how to do this, I do not see an option in fdisk, perhaps it is mkfs that needs the setting to be changed.  I will try to check the man pages to see if I can figure it out.

Also I'm currently downloading the ISO for Pmagic, as a backup 'backup' plan.

---

### Post by srs5694 on 2011-09-03
It looks like mkfs.xfs (the program that gets called when you use mkfs with "-t xfs") may have a problem with your disk's sector size. There's nothing you can do about this in fdisk, but there may be a mkfs or mkfs.xfs option that would work. Glancing at the mkfs.xfs man page, you might try this:

```

sudo mkfs.xfs -s size=4096 /dev/sdh1

```

I make no guarantees that this will work, though.

Another option would be to try another filesystem; perhaps its filesystem creation tool would be less fussy. Assuming they'd all work, ext3fs is the safest choice, and ext4fs would also be safe on modern systems, but you might want to research its stability on your relatively old installation first. JFS is also an option, although my personal experience is that it's a bit less stable than XFS or ext2/3/4fs. I've always liked ReiserFS on disks that hold small files, but for your purposes I'm not sure it's the best choice.

---

### Post by morilibus on 2011-09-03
That did the trick, thank you for all your help.

Case closed.

[EDIT]
Ok I thought it all looked good, so I started to copy stuff over for back up, and it said not enough space, current free space is 746.4 GB.

Under disk utility it does show the full amount.

Sigh.... so close.

any ideas?  I could try the ext3 I suppose, or I could go ahead with booting via parted Magic and see what that can do.

[UPDATE]

I tried using ext3 and that reduces the space to 697.3GB...

Going to try the Parted Magic now, so I may be MIA for the next little bit.

---

### Post by srs5694 on 2011-09-03
> **morilibus said:**
> That did the trick, thank you for all your help.

Do you mean the mkfs.xfs command I suggested?

> Ok I thought it all looked good, so I started to copy stuff over for back up, and it said not enough space, current free space is 746.4 GB.

Please post the output of the following commands under your normal Ubuntu 9.10 boot:

```

df -h
sudo fdisk -lu /dev/sdh
sudo parted /dev/sdh print

```

The output of the same commands from Parted Magic, particularly after you've mounted /dev/sdh1, might provide an informative contrast; it could be that there's a bug lurking somewhere in the kernel or some other piece of software in Ubuntu 9.10 that's causing problems but that's been fixed more recently.

---

### Post by morilibus on 2011-09-03
> **srs5694 said:**
> Do you mean the mkfs.xfs command I suggested?
Yes, sorry I should have mentioned what part did resolve(so I thought) the problem.

I've just created a Parted Magic Boot disc which I first tried to make using my usb stick, which imaged fine, bot I cannot boot into it(may it too is too old)...so I made a bootable cd on my windows machine(as my ubuntu machine has only a read Drive, then I did a backflip(not really) as it seemed to be next logical thing to do after jumping through so many hoops.

The disc has completed so I will try booting into it shortly.

I have to use a vitual box running windows in order to be able to login to this ubuntu forums in order to reply to this thread.  As my ubuntu machine is unable to reach the login portion of the site, along with gmail and similar sites that require a login.  But that is another problem: [http://ubuntuforums.org/showthread.php?t=1838010](http://ubuntuforums.org/showthread.php?t=1838010), one that I thought was a networking issue which has now turned into the fact that my machine may have been hacked.  Hence the need to back up, and install a newer more secure ubuntu.... but I digress.

**df -h**
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              46G   28G   16G  65% /
udev                 1007M  372K 1006M   1% /dev
none                 1007M  100K 1006M   1% /dev/shm
none                 1007M  536K 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda2             184G   18G  157G  11% /home
/dev/sdh1             735G  197M  698G   1% /media/External
/dev/sdi1             990M  172M  818M  18% /media/BOOT
/dev/sr0              172M  172M     0 100% /media/cdrom0

```**fdisk -lu /dev/sdh**
```
Note: sector size is 4096 (not 512)

WARNING: The size of this disk is 3.0 TB (3000558944256 bytes).
DOS partition table format can not be used on drives for volumes
larger than (17592186040320 bytes) for 4096-byte sectors. Use parted(1) and GUID 
partition table format (GPT).


Disk /dev/sdh: 3000.6 GB, 3000558944256 bytes
255 heads, 63 sectors/track, 45599 cylinders, total 732558336 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63   732558335  2930233092   83  Linux

```**parted /dev/sdh print**
```

Warning: Device /dev/sdh has a logical sector size of 4096.  Not all parts of
GNU Parted support this at the moment, and the working code is HIGHLY
EXPERIMENTAL.

Error: Can't have a partition outside the disk!  
```

onto the boot cd, I shall return.

thanks again for your continued assistance...

---

### Post by morilibus on 2011-09-03
And I'm back...

Everything seemed to go ok on the Parted Magic side of things, set up the new drive with xfs filesystem.

REBOOT

cannot mount drive:

```
Error mounting: mount exited with exit code 32: mount: /dev/sdh1: can't read superblock
```[B]fdisk -lu /dev/sdh
[/B]```
Cannot open /dev/sdh
```So this does seem to be my OS build that seems to be the weakest link.

Can't back up data without first upgrading OS, can't upgrade OS till I backup data.

Is there anything I can update within ubuntu 9.10 that would allow it to read these larger drives?

I have no updates showing in the update manager.

[Edit]
Me - "Hey murph, how's it going?"

Murphy - "Things don't seem to be working out for you huh, anything more I could F up for you?"

Me - "No I think you've done enough... Oh wait my Internet just went down, kudos you got me again, oh you!"

Now accessing forum from Phone, and on a 2+ hour wait with tech support.

---

### Post by srs5694 on 2011-09-04
It's possible that Parted Magic is assigning your device filenames differently, so what's /dev/sdh in your regular Ubuntu installation might be something else in Parted Magic. It's worth checking this out. Try unplugging the disk, doing an "ls /dev/sd?", plugging the disk back in, waiting a few seconds, and repeating the "ls /dev/sd?" command. You should see the disk's new device filename, and that should enable you to use fdisk on it.

That said, it is starting to look like a kernel issue. You might be able to resolve this in Ubuntu 9.10 by compiling a more recent kernel yourself. This is an involved enough task that I can't give you a step-by-step procedure, but there are plenty of online guies. [This one](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html) turned up in a Google search, for instance.

Another option might be to use the Parted Magic CD to prepare the disk and perform your backup. You'll obviously need to get it working better from Parted Magic to do this, though.

Trying another filesystem from Ubuntu 9.10 is also worthwhile.

---

### Post by morilibus on 2011-09-04
And I'm back.  Sorry just now got internet back up and running after running a new line out to pedestal in my alley.  Got to love 40 year old homes.

With the Hard drive unplugged, the ls /dev/sdg (as I actually have two of these hard drives, so one is sdh and one is sdg, right now just the fiddling with the g.) gives the following(if I'm understanding correctly).

**Unplugged**
```
marc@Tri-Serv:~$ ls /dev/sdg
ls: cannot access /dev/sdg: No such file or directory

```**Plugged in**
```

marc@Tri-Serv:~$ ls /dev/sdg
/dev/sdg

```The drive(s) do show up still in the GUI Disk Utility, and show the correct size and filesystem, but they will not mount.

I did try both ext3 and xfs filesystems within ubuntu, both produced a reduced capacity drive, as noted earlier I believe.  If that is what you meant, or did you mean try a different filesystem with parted magic( currently did both as XFS)?

The one problem with backing up everything within the parted magic boot is that the data is a software raid, and that doesn't show up.  Unless I can re-setup the raid within Parted Magic.  But I'd be worried about messing something up and losing my data.

I may try hooking the drives up to a networked PC and transfer everything over the network.  However all my PC are running XP and I have a feeling they won't like the large drives either. ALthough I could load ubuntu 11.04 on to one of the other PC's(or even just do it over the live cd?), and then transfer everything over... and I Imagine that would take quite a while.

I'll check out the link and see what is involved with recompiling the kernal.

Again thanks for your help.

[UPDATE]

Through a huge workaround I've manage to start the transfer of data from my Raid-5 to my 3T external drives. currently transferring at a whooping 3.5 MB/s...

The method right now is the following:

[LIST]
[*]create a virtual box using 'Sun VirtualBox' running ubuntu 11.04
[*]tried to install virtual box additions which would allow my to share a host folder with the client - FAIL
[*]Try to connect from client to host using ssh - FAIL
[*]change network adapter from NAT to Bridge
[*]connect to Host machine using samba file sharing
[*]transfer files over network to client...
[/LIST]
Now it is working, but its going incredibly slow... considering the hardware connections are, SATA drive on one machine going to USB drive on same machine. and Transfer is going from Sata drive to Router, back to virtual machine onto USB external drive.

So clearly not the most efficient way of doing it, but it is at least working.

I still might try  recompiling the kernal, and if not will just continue the epically slow transfer and leave it be for a couple weeks to transfer...


[UPDATE]

Ok I looked into recompiling the kernal, and it doesn't look like something I should attempt, especially with the risk of having to re-install from scratch and thus possible mucking up my raid and losing data(which the whole purpose of this escapade is to back up said data).

So I guess its 2 weeks of network transfering, unless I can ge tthe guest services thing to work on the virtual box to perhaps be able to transfer straight through the system.

[UPDATE]
Got Virtualbox Additions working(tried a newer version (4.1.2) than the one I had previously used (3.1.8)
Still only transferring at 3.5 MB/s, maybe thats as fast as I'm going to get with this workaround.

---

### Post by morilibus on 2011-09-08
Update

loaded Ubuntu 11.04 on a different machine and hooked up one drive to it and am transferring data from the 9.10 machine over the network.  Speed is peaking at around 18MB/s.

and still transferring to the other drive through the virtual box which is peaking at around 4.5MB/s.

So now it should only take a few days instead of a few weeks.

good enough for me.

thanks for the Help.

case closed

Solution= ubuntu 9.10 does not support large drives

---

