---
title: "Problem creating filesystem"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by TheArchedOne on 2012-01-14
Hi,

I'm trying to add a new drive using webmin on ubuntu server 11.10. I've wiped existing partitions, created a primary partition and have the following partition info:

Number | Type  | Extent | Size      | Start | End   | Used by   
1      | Linux |        | 238.47 GB | 1     | 30402 |

When I try to create an ext3 filesystem with default settings on this partition, I get the following error:

```
Executing command mkfs -t ext3 -q /dev/sda1partprobe ; mkfs -t ext3 -q /dev/sda1 ..

Could not stat /dev/sda1partprobe --- No such file or directory

The device apparently does not exist; did you specify it correctly?
```

Please can someone help me out here as I have no idea how to get found this.

Thanks

TAO

---

### Post by darkod on 2012-01-14
Are you trying remotely trough SSH, or trough Webmin?

I haven't used Webmin, so I have no idea if it is not executing the right command.

Otherwise, provided the partition was created correctly, the command to create the ext3 filesystem is:
sudo mkfs -t ext3 /dev/sda1

Be careful, in your case the disk might not be sda because you are adding a new disk on top of the existing ones. Make sure you use the correct partition in the command.

---

### Post by TheArchedOne on 2012-01-14
Thanks darkod. I was doing it via webmin. I've just tried running your the command you suggested at the command line and it seems to have worked. How can I check that it worked correctly?

---

### Post by darkod on 2012-01-14
sudo parted /dev/sda print

will print all partitions on the disk and their filesystem (I think).

---

