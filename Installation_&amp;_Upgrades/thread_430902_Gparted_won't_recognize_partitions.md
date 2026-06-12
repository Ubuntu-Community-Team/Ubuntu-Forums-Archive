---
title: "Gparted won't recognize partitions"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by atari2600a on 2007-05-02
Sorry to be the (probably) millionth person to ask this...

I'm trying to install 7.04 onto my laptop, & when I try to partition the hard disk in gparted, it fails to see any of my 4 exsisting partitions & marks all ~55GB as unformatted.

This is how I currently have my hard disk set up:

-FAT16 partition, under 10MB, used for Dell BIOS-accesed diangostic testing
-FAT32 Partition, same as above.  I probably don't need these partitions at all but I wouldn't want to take the risk of finding out how my BIOS would react without them
-NTFS partition, ~50GB, contains my Vista Ultimate install
-NTFS partition, ~5GB, contains an old XP install I kept just in case my primary XP install crapped out.  This is the partition I wish to get rid of.  Vista also seems to have installed some system files on here too, but just using the repair function on the install DVD should replace any files lost.

What I plan on doing is deleting my small NTFS partition, putting an extended partition in it's place, putting the ext3 & a 512MB swap partition (512MB is all I really have room for as of now), & then installing like that.

So can anyone help me out here?

---

### Post by jack1254 on 2007-05-02
My first instinct is to say try a different partitioner. It may be a problem (somehow) with GParted... qtparted works well enough for me, but I'm running Kubuntu so I don't know how many dependencies you would need to download, if it's few, run at the command line:

```
sudo apt-get install qtparted
```

Searching the package manager for a partition tool might reveal something faster to install.

Also, on another note, I have left the ~50MB FAT16 Dell Partition on my drive (the diagnostics might come in hand some day), but have long deleted the bigger one without any problems.

---

### Post by atari2600a on 2007-05-02
Don't forget, I'm still running off the liveCD, so I don't really think I can *install* anything, more or less just run things.

---

### Post by zvacet on 2007-05-02
Download Gparted live CD and you will do the job.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by atari2600a on 2007-05-03
Still isn't pulling up anything.

---

### Post by DavidTangye on 2007-05-03
I might have a related problem with gparted. It flags my root partition with a warning icon: "Unable to find mountpoint.

My /etc/fstab :
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=b7bce030-9b6a-43a4-9eb1-fbca1bdde76a / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=e9abaaf0-de55-4552-a625-e5d05329b077 /home ext3 defaults 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=081727d9-f4da-4060-b837-f7ec7dc17950 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=9877-489A /mnt/winfat vfat rw 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=1A6409D86409B811 /mnt/windows ntfs ro,users,umask=0000 0 0

Gparted does recognise the partitions though, including the last two fat and ntfs partitions.

---

### Post by JohnnyVW on 2007-05-03
> **DavidTangye said:**
> I might have a related problem with gparted. It flags my root partition with a warning icon: "Unable to find mountpoint.

My /etc/fstab :


Gparted does recognise the partitions though, including the last two fat and ntfs partitions.

I'm getting the same message.  Here's my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1 -- converted during upgrade to edgy
UUID=18ddd9f8-c222-4d16-8a92-07b2dcbeb205 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdd5 -- converted during upgrade to edgy
UUID=58ad3e63-546c-490a-a33c-16b7526f7834 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=7C1C3DA61C3D5C78 /media/windows1 ntfs nls=utf8,umask=0222 0 0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=50E87B02E87AE61E /media/windows2 ntfs nls=utf8,umask=0222 0 0

```

Any ideas?  :confused: 

There was a problem with swap too, but I re-formatted the swap partition as swap.  The exclamation point disappeared in GParted on the swap partition, but it's there on hdd1.

Attached is a screen shot of GParted.

---

### Post by finalzero on 2007-05-03
Install 6.10 from the live cd, 6.10's partition manager works much better than 7.04's and will recognize your existing partitions allowing you to correctly configure any new linux ones.

Then boot into Gnome but don't do any updates, just wait for the upgrade option and allow it to do an upgrade to 7.04.

This will result in the upgrade recognizing your partition setup and preserving the layout - I found trying to do a clean install of 7.04 a nightmare, it makes a mess of the partitions and when it does install it then fails to recognize the drives or partitions so you end up with a bricked system.

---

### Post by atari2600a on 2007-05-04
STILL nothing.

---

### Post by atari2600a on 2007-05-04
STILL more nothing.  Every attempt is like a castrated man trying to conceive a child...with another castrated man.

Does anyone here have any idea what's going on?

---

### Post by JohnnyVW on 2007-05-05
Seems Grub takes forever to come up with its boot menu too...

---

