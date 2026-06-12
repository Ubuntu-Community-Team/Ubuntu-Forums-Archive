---
title: "[SOLVED] New Raid0 using mdadm"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by celestius on 2008-03-06
I do have a couple questions at the end if anyone here cares to answer them. Thanks in advance for that. Now, on with the show!

So I installed Linux. Yay. I came from a Windows Vista install that had a primary drive for system files and then a FakeRaid setup in Raid0 mode for all my data. For some reason Linux wouldn't recognize the existing NTFS partition on the raided drives so I decided to backup my data and reformat the raid and use  mdadm instead. Just thought I would share what I did for the good of the community. Oh and in order to get my data backed up I had to install a temporary copy of windows on another drive and transfer the data from there in case someone came here looking for info about that. This is strictly info about setting up a Raid0 on two SATA drives. So my goal was to get a Raid0 setup on two SATA drives using mdadm formatted with the reiserfs filesystem.

First I disabled the raid features in my bios for my particular FakeRaid.

Then I booted into Ubuntu and fired up gparted. This is a partition editor for Linux. If you don't have it you should be able to install it with the following command:

```
$ sudo apt-get install gparted
```

Then you can look for it in your system menu or just type gparted in a commandline.

Ok so my drives showed up in parted and I formatted each of them.  I don't know if it matters what filesystem you use for formatting because they get formatted when they're part of the raid later but just to be safe I used reiserfs here as well. After formatting them, I set the raid flag for the partitions. The option to set the flag can be found in the "Partition" menu under "Manage Flags".

Great, now my drives are both formatted and have the raid flag set. You can verify this by typing:

```
$ sudo fdisk -l
```

which should show something like the following:

```
Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90989098

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4310    34620043+  83  Linux
/dev/sda2            4311        4500     1526175    5  Extended
/dev/sda5            4311        4500     1526143+  82  Linux swap / Solaris

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007edc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9039    72605736   fd  Linux raid autodetect

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028f7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9039    72605736   fd  Linux raid autodetect

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x000342eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       15505   117217768+   7  HPFS/NTFS

```

I actually have four drives in my system but the ones I'm setting up for raid are /dev/sdb and /dev/sdc. Notice how they have "Linux raid autodetect" listed under system.

Ok now we have to switch over to mdadm and setup the raid array. Go ahead and install mdadm if you haven't already:

```
$ sudo apt-get install mdadm
```

Then execute the following command to get the array configured. 

```
$ sudo mdadm --assemble --scan
```

Now, I'm guessing that mdadm used the flags set on the partitions to identify them and use them for the raid. Alternatively you can use this command to configure the raid manually: 

*NOTE - You only need to do the previous command or this one, not both.

```
$ sudo mdadm --create /dev/md0 -chunk=4 --level=0 --raid-devices=2 /dev/sdb /dev/sdc
```

Mdadm should give you a message similar to the following:

```
mdadm: /dev/md/0 has been started with 2 drives.
```

Even though mdadm stated that "/dev/md/0" was created when you actually use the new raid volume you have to use it without the slash bewtwen d and 0. For example, if I wanted to mount the drive on my system the command would be "sudo mount /dev/md0 /media/Data" 

You may have to change the options to fit your needs like the names of the drives you're trying to raid or the number of devices etc. The chunk size has to do with how big the pieces are that the data is split up into as it's stored on the drive. Do some reasearch if you want to know more about this and what size is good for your needs. Also, I don't know why the raid is named md0. That's just what worked. Maybe someone else can let us noobs know if it has to be 0 or if that's just an arbitrary number that can be assigned.

Anywho, now we have a raid array setup with the two drives. You can verify that the drives are in the array and see general info about the array by typing:

```
$ sudo mdadm --misc --detail /dev/md0
```

Last thing we gotta do now is partition and format the new raid disk /dev/md0 that we just created. First, we go into fdisk and write the partition table (enter w when it asks for a command):

```
$ sudo fdisk /dev/md0
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xb8d75e9b.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 36302816.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```

The computer sez reboot so reboot succa! Now that's a good little automaton.  Now enter this command to format your drive:

```
$ sudo mkfs -t reiserfs -l Data /dev/md0
```

Joy!

Ok so now the drive is created and partitioned and formatted so I created a folder in /media with the root account (sudo nautilus) called Data and mounted the drive with:

```
$ sudo mount -t reiserfs /dev/md0 /media/Data
```

I had to change the permissions on that folder after I created it to be readable and writeable for everyone in order to write from it from my standard login and not just the root login. I do kinda have a question at this point if anyone can help me out. I'm pretty noobish at Linux so don't hate lol. This is what my /etc/fstab looks like:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a2b63d69-732c-4e66-820a-5cd2ec99c53e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=88d37555-4d72-450d-84ee-d484955902e1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/md0	/media/Data	reiserfs	none	0	0
```

Any time i reboot I have to manually run the previously mentioned mount command to get the drive to mount and show up in my gui and all that good stuff. Is there a way to have the drive auto mount without me having to run this command? Also, if there is a command to have this raid drive mount automatically are there any issues that I might run into if I put my account's home directory on it?

I'm running Ubuntu x64 7.10 with gnome.

Bye!

Oh also if anyone notices a problem with these instructions lemmie know. I followed them as I was typing them on my system so I know they worked for me but I'll be happy to update them if there's an issue with specific hardware or whatever.

---

### Post by ssj3strife on 2008-03-08
When you reboot your system, do you have to manually reassamble md0? If not, an entry in your fstab should do the trick. Try changing on the last line the word "none" to "defaults" and see if that does the trick.

---

### Post by bsmith1051 on 2008-03-08
You're setting-up a RAID-0 stripe?  or, did you mean a RAID-1 mirror?  I thought people usually setup mirrors, not stripes.  Also, in your instruction re mdadm I think you had a typo,
"mdadm: /dev/md/0 has been started with 2 drives" should say "/md0" shouldn't it, i.e., without an extra / symbol?

---

### Post by celestius on 2008-03-11
you da man ssj. i was just having to $ sudo mount /dev/md0 /media/Data every time after a reboot. the raid was staying built but the "defaults" setting in the fstab worked like a charm.

i was setting up a striped raid array because i wanted to  have a high performance data volume to work from. that was why i wrote this guide because mostly everywhere i looked on the forums people *were* doing mirrors not stripes and if they weren't using mirrors they were using raid5. i suppose if i had a gajillion dollars i would go buy a couple more raptors and use those for data redundancy but the stuff i'm keeping on this volume isn't all that important so backups won't be critical. :) oh yeah and i thought it was kinda funny about the md/0 output from mdadm but i copied and pasted that directly from the console as I configured it. i'll make a note in the tutorial about that.

thanks for the reply yall!

---

### Post by ssj3strife on 2008-03-12
I'm glad that solved it, otherwise we would have had a real problem on our hands... :)

You also might want to look into the "noatime" option. By default, every read from the disk updates the last access time - which means, every "read" turns into a "read/write," which will slow disk access considerably. If you're going for performance - which it sounds like you are - then noatime is definitely your friend.

Nice guide, thanks for taking the time to write it. Take care!

---

