---
title: "fsck error after update"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by EvilBro on 2008-05-18
I've just updated from Gutsy to Hardy. During startup I get the following message (which I've copied from checkfs in /var/log/fsck):

```
Log of fsck -C3 -R -A -a 
Sun May 18 16:36:02 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such file or directory while trying to open /dev/hdc1

/dev/hdc1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sun May 18 16:36:02 2008
```

I get some kind of prompt during startup, but when I exit this prompt, ubuntu continues startup and everything seems to work. What I figured is that this had to do with the second hd in the machine. I was therefore surprised that I could access this hd.

Does anyone know how to fix this?

P.S. if I remember correctly, I added the automounting at startup of this drive myself. I unfortunately have no idea anymore about actually how I did that...

P.P.S. I think the drive it is confused over is not the second hd... I think its the cdrom now. Doesn't help me further though...

---

### Post by forestpixie on 2008-05-18
can you check that the UUID for the drives in fstab are correct

```
sudo blkid
cat /etc/fstab
```

I got that when I changed a partition but forgot to deal with fstab

If they don't match edit fstab

---

### Post by EvilBro on 2008-05-18
> **forestpixie said:**
> can you check that the UUID for the drives in fstab are correct
I did that just now and noticed the second drive entry. I deleted it to see what would happen and now everything seems fine. Guess it was the second drive after all then.

> blkid
It gives me a list of devices all starting with 'sd'. In fstab everything starts with 'hd'. What gives?

---

### Post by forestpixie on 2008-05-19
Not sure why you would have both - but I can say that reporting discs as hda changed about the time of feisty/gutsy.

It now reports all as scsi but it's ok apparently

---

### Post by Can0n on 2008-05-21
I have the same error and I have to press CONTROL+D to boot Ubuntu.

My /var/log/fsck/checkfs:
> Log of fsck -C3 -R -A -a 
Wed May 21 14:26:46 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Bad magic number in super-block while trying to open /dev/sdc1

/dev/sdc1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/sdb5: clean, 108699/18317312 files, 28395987/36620159 blocks
fsck died with exit status 8

Wed May 21 14:26:47 2008
----------------

My fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d1d57803-5d80-412d-ab9e-1de5184b2a62 /               ext3    errors=remount-ro 0       1
# /dev/sda5
UUID=84a200ee-bfd1-4a68-b41c-010b844bd6b5 /home           ext3    defaults        0       2
# /dev/sda1
UUID=D6943D01943CE621 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=016f6473-9023-4853-a183-6869677c843a none            swap    sw              0       0

/dev/sdc1	/media/usb	ext3	defaults	0 	1

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

My blkid:
> /dev/sda5: UUID="ea212fb0-6892-46b5-a1b2-6b51d11a944a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="D6943D01943CE621" TYPE="ntfs" 
/dev/sdb5: UUID="84a200ee-bfd1-4a68-b41c-010b844bd6b5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="d1d57803-5d80-412d-ab9e-1de5184b2a62" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: TYPE="swap" UUID="016f6473-9023-4853-a183-6869677c843a" 
/dev/sdc1: UUID="0000-0000" TYPE="vfat"

---

### Post by zvacet on 2008-05-21
Your UUID for sda5 doesn´t match.Replace one from fstab with UUID from blkid.

---

