---
title: "Trying to install dual boot Ubuntu/Ubuntu server"
date: 2012-07-22
forum: Installation &amp; Upgrades
---

### Post by FarRed on 2012-07-22
I already installed minimal Ubuntu server (command line only), using  about half the disk space.  When I tried to install Ubuntu to make a  dual boot, however, it can't see the server install or partitions.  It wants to use the entire disk.  I  would have expected this from Windows, but not Linux.  These are both  the latest releases.   Any idea what I might be doing wrong?

---

### Post by darkod on 2012-07-22
Did you install with something like LVM?
The standard live cd wouldn't be able to see LVM. Also, if there is some error or corruption in the partition table, it will only offer to use the whole disk, not being able to see any existing installation.

Another reason might be if you have raid meta data remains on the disk (if it was used in hardware raid / fakeraid before), in that case the installer will be confused whether you are running a raid or not.

You can start by printing the partitions with:
```
sudo parted -l
```

What does that show?

---

### Post by FarRed on 2012-07-22
Yes, I was using LVM.  There may have been an easier way, but since it was a brand new install, I simply re-installed server   I re-ran the ubuntu install and it recognized the server partitions.  Thanks.

---

