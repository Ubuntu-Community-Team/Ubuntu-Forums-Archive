---
title: "FakeRaidDebug, No RAID disks, told to post here"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by Jeinhor on 2007-08-17
Hello,

Im trying to setup a PRIMERGY RX100S4 server on Ubuntu with the RAID controller on the server. It is an LSI MegaRAID controller, and I tried to follow the FakeRaidHowto at [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) to set it up correctly. I got the message No RAID disks and I followed the instructions for this message at FakeRaidDebug.

Heres the output from fdisk -u -l /dev/sda:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

Disk /dev/sda doesn't contain a valid partition table
```

I would really like to get the server running on the onboard RAID controller as it is a production server, and I would to minimize its downtime. When using the onboard RAID controller I can hot swap the disks, something that is not possible in pure Ubuntu Software RAID.

Please advice,
Thanks in advance.

---

