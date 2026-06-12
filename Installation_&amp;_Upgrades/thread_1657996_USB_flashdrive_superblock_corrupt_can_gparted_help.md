---
title: "USB flashdrive superblock corrupt: can gparted help?"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2011-01-02
I'm trying to format a 32GB USB flash drive to ext3 for Linux.

```
sudo tail -f /var/log/messages
```shows me:

Jan  1 23:40:42 rj kernel: 
[13773.966516] sd 11:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[13800.780008] usb 2-1: new high speed USB device using ehci_hcd and address 8
[13800.932141] usb 2-1: configuration #1 chosen from 1 choice
[13800.932281] scsi12 : SCSI emulation for USB Mass Storage devices
[13805.932983] scsi 12:0:0:0: Direct-Access              Flash Disk       5.00 PQ: 0 ANSI: 2
[13805.933279] sd 12:0:0:0: Attached scsi generic sg3 type 0
[13805.933911] sd 12:0:0:0: [sdc] 65536000 512-byte logical blocks: (33.5 GB/31.2 GiB)
[13805.934498] sd 12:0:0:0: [sdc] Write Protect is off
[13805.936223]  sdc: sdc1
[13805.939802] sd 12:0:0:0: [sdc] Attached SCSI removable disk

And then hangs.

```
sudo fsck /dev/sdb1
```shows me:

fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Trying that last suggestion gives me the exact same message. Same using -b 16384

Palimpsest Disk Utility shows:
34 GB Unrecognized
Unknown or Unused

My general question is: [B][I]how can I fix the corrupted superblock and do the format?

[/I][/B]*[Apologies if this is the wrong forum for the question.]*

---

### Post by watchpocket on 2011-01-02
Maybe I should simply ask if there's any hope for a USB stick if it has a "bad superblock."

Is it repair-able? 

If it is, formatting should be possible.

---

### Post by SteveDee on 2011-01-02
I don't know if this will help, but...

Open Synaptic and install: pysdm
In a terminal type:-
```

sudo pysdm

```

Select your USB device from the Partition list...

---

### Post by ottosykora on 2011-01-02
actually it is nothig that unusual and does not mean everything is broken or so.
You can just run the fschk again, the drive must be unmounted during the check.

If nothig helps, you simply reformat the flash, that is it. But as I said, it will well work even with the error, this quite common for flash. All those file systems were designed for magnetic , rotating drives, flash have completely different way of internal file system and the for us 'common' ext3 or vfat or ntfs or what ever is only kind of virtual on the top of the internal flash file system. Some of the error messages are resulting from all that.
I used to work in manufacturing of linux based servers, they were run from flash all, similar errors I got all the time, still the servers run fine for many years already.

---

### Post by watchpocket on 2011-01-03
I re-formatted, can't get it to mount, though:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1, 
missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
``````
dmesg | tail:
[ 2499.371538] sd 8:0:0:0: [sdb] 65536000 512-byte logical blocks: (33.5 GB/31.2 GiB)
[ 2499.372112] sd 8:0:0:0: [sdb] Write Protect is off
[ 2499.372115] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 2499.372117] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 2499.373782] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 2499.373785]  sdb: sdb1
[ 2499.376378] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 2499.376380] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 2499.453408] JBD: no valid journal superblock found
[ 2499.453410] EXT3-fs: error loading journal.
```

---

### Post by watchpocket on 2011-01-04
>  it will well work even with the error

How will it work if it's not mounting?

---

