---
title: "ext3 creation failed"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by ecoppel on 2007-12-31
I got a new hard drive for Christmas, and tried installing Kubuntu on it today.  It stalled about 5% of the way through the partitioning part of the process.  I got a message that said something about ext3 failing, and froze hard.  I couldn't even move the cursor.

Now the LiveCD isn't recognising the hard drive at all.  It just doesn't think it's there.

fdisk -l gave me no response at all.

/dev has two screens worth of stuff, none of which has anything to do with a hard drive.

dmesg |tail gave me this:
```
[  237.175691] eth0: no IPv6 routers present
[  360.910547] JFS: nTxBlock = 4026, nTxLock = 32213
[  361.309067] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[  361.335360] SGI XFS Quota Management subsystem
[  361.905416] program parted_devices is using a deprecated SCSI ioctl, please convert it to SG_IO
[  361.949070] end_request: I/O error, dev fd0, sector 0
[  361.973057] end_request: I/O error, dev fd0, sector 0
[  399.136392] program parted_devices is using a deprecated SCSI ioctl, please convert it to SG_IO
[  399.182859] end_request: I/O error, dev fd0, sector 0
[  399.206838] end_request: I/O error, dev fd0, sector 0
```

I googled the bit about a deprecated SCSI ioctl, and it seems to be an open bug with ubiquity.  What I don't know is what I can do about it, or if the hard disk is recoverable.

Please help?

---

