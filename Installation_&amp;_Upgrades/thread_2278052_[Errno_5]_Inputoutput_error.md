---
title: "[Errno 5] Input/output error"
date: 2015-05-13
forum: Installation &amp; Upgrades
---

### Post by Joel_Kingsley on 2015-05-13
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
I get this error whenever I try to install Ubuntu 14.04 from live usb(try Ubuntu before installation). I previously used the same iso file(ubuntu-14.04.1-desktop-amd64.iso) for installing Ubuntu which I uninstalled inorder to change to windows 7. How do I fix this error?

---

### Post by ubfan1 on 2015-05-13
Did you ever run the "media check" choice on the live-media?  Memory check is also a good thing to run.  Maybe from the "try Ubuntu" choice, partition and format the disk before you attempt the install.

---

### Post by Joel_Kingsley on 2015-05-13
> **ubfan1 said:**
> Did you ever run the "media check" choice on the live-media?  Memory check is also a good thing to run.  Maybe from the "try Ubuntu" choice, partition and format the disk before you attempt the install.
Thank you for the quick response. I already tried 'check for disk defects' during boot from live media, and had no defects. I fully formatted the 1.0 TB disk and tried through 'erase and install Ubuntu 14.04' and customized partitions through 'something else', but no improvement. I also ran memtest86+ with 0 errors.

---

### Post by Bashing-om on 2015-05-13
Joel_Kingsley; Hello;

I have to wonder if this drive was ever used in a raid (LVM) configuration ? The desk top installer will not deal with that embedded meta data.
A quick way to check:
```

sudo wipefs /dev/sda

``` where 'sda' is the 1st hard drive, the 2nd hard drive would be 'sdb'
Note that you should not just trust me that that command is safe (even though it is), you should run "man wipefs" and confirm for yourself that the command will just list all visible filesystems (and in this case, RAID metadata) and their offsets. 

My return: wipefs: WARNING: /dev/sdb: appears to contain 'dos' partition table; as I have removed the raid meta data from my drives, no meta data (offset info ) is returned.

[INDENT][INDENT]it's just a thought
[/INDENT][/INDENT]

---

### Post by Joel_Kingsley on 2015-05-13
> **Bashing-om said:**
> Joel_Kingsley; Hello;

I have to wonder if this drive was ever used in a raid (LVM) configuration ? The desk top installer will not deal with that embedded meta data.
A quick way to check:
```

sudo wipefs /dev/sda

``` where 'sda' is the 1st hard drive, the 2nd hard drive would be 'sdb'
Note that you should not just trust me that that command is safe (even though it is), you should run "man wipefs" and confirm for yourself that the command will just list all visible filesystems (and in this case, RAID metadata) and their offsets. 

My return: wipefs: WARNING: /dev/sdb: appears to contain 'dos' partition table; as I have removed the raid meta data from my drives, no meta data (offset info ) is returned.
[INDENT][INDENT]it's just a thought
[/INDENT]
[/INDENT]

man wipefs result:

WIPEFS(8)                    System Administration                   WIPEFS(8)

NAME
       wipefs - wipe a filesystem signature from a device

SYNOPSIS
       wipefs [-ahnpV] [-o offset] device

DESCRIPTION
       wipefs can erase filesystem or raid signatures (magic strings) from the
       specified device to make the filesystem invisible for libblkid.  wipefs
       does  not  erase  the  filesystem  itself  nor  any other data from the
       device.  When used without options -a  or  -o,  it  lists  all  visible
       filesystems and the offsets of their signatures.

OPTIONS
       -a, --all
              Erase all available signatures.

       -h, --help
              Print help and exit.

       -n, --no-act
              Causes everything to be done except for the write() call.

       -o, --offset offset
              Specify the location (in bytes) of the signature which should be
              erased from the device.  The offset number may  include  a  "0x"
              prefix;  then the number will be interpreted as a hex value.  It
              is possible to specify multiple -o options.

              The offset argument may be followed  by  binary  (2^N)  suffixes
              KiB,  MiB, GiB, TiB, PiB and EiB (the "iB" is optional, e.g. "K"
              has the same meaning as "KiB") or decimal  (10^N)  suffixes  KB,
              MB, GB, PB and EB.

       -p, --parsable
              Print  out  in parsable instead of printable format.  Encode all
              potentially unsafe characters of a string to  the  corresponding
              hex value prefixed by '\x'.

 -V, --version
              Output version information and exit.

AUTHOR
       Karel Zak <kzak@redhat.com>.

AVAILABILITY
       The  wipefs  command is part of the util-linux package and is available
       from [ftp://ftp.kernel.org/pub/linux/utils/util-linux/](ftp://ftp.kernel.org/pub/linux/utils/util-linux/).

SEE ALSO
       blkid(8) findfs(8)

util-linux                       October 2009                        WIPEFS(8)
 Manual page wipefs(8) line 18/60 (END) (press h for help or q to quit)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
What should I do know? And yes I did use it in a LVM configuration once after this error.

---

### Post by Bashing-om on 2015-05-13
Joel_Kingsley; Welp;

If you understand the 'wipefs' command:
I do suggest ya go ahead and run it and see what there is on that drive for meta data.
```

sudo wipefs /dev/sda

```
If more than the one hard drive:
```

sudo wipefs /dev/sdb

```

Maybe nothing
[INDENT][INDENT]but, a cheap check; just to be sure
[/INDENT][/INDENT]

---

### Post by Joel_Kingsley on 2015-05-14
sudo wipefs /dev/sda
wipefs: WARNING: /dev/sda: appears to contain 'gpt' partition table
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
I again ran check disk for defects and got 1 defect. Thank you for your patience.

---

### Post by Joel_Kingsley on 2015-05-14
> **Bashing-om said:**
> Joel_Kingsley; Welp;

If you understand the 'wipefs' command:
I do suggest ya go ahead and run it and see what there is on that drive for meta data.
```

sudo wipefs /dev/sda

```
If more than the one hard drive:
```

sudo wipefs /dev/sdb

```

Maybe nothing[INDENT][INDENT]but, a cheap check; just to be sure
[/INDENT]
[/INDENT]


Now after creating a new partition table in gparted, I ran sudo wipefs /dev/sda and got

wipefs: WARNING: /dev/sda: appears to contain 'dos' partition table

What to do next?

---

### Post by ubfan1 on 2015-05-14
Looks like you have successfully changed the partition table type, so now think about what partitions you want on the install.  The default is one root partition and one swap partition, which is not really good on a 1T disk.  Have a swap partition.  The root partition may be 30G-50G, and you may make two that size so in the future, you may install a new system and test it out before moving off the old system.  I think your system is not UEFI, so no special EFI partition is needed.  The bulk of the space you may make a data partition for your files, which may be mounted and access via a link from your home directory.  Some recommend a home partition, but if you ever put two different OSes on the disk, you really do not want to share the home, because of all the hidden directories with application version specific files.
  You mentioned Windows 7.  Is that to go on this 1T disk?  If so, install it first.  I am finding I would like a few FAT partitions for experimenting with, so two 1G FAT partions would be optional.  Depends entirely upon your needs, and of course, you may change things in the future (after backing things up of course).

---

