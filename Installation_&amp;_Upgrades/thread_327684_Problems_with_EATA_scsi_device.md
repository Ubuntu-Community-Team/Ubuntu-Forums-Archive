---
title: "Problems with EATA scsi device"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by gjngeldenhuis on 2006-12-29
Hi All,
I have spend the best part of a day trying to get Ubuntu(ubuntu-6.10-server-i386) to work on a old PII with a DPT scsi controller. I read somewhere that you should use the EATA kernel driver which I did. 

When beginning to install, the software does not detect the harddrives, I have to manually select the EATA driver/module and then it works just fine and I can continue with the installation.

Everything works beatifully and then when I reboot it just fails. Grub hangs in the air with the following message:
Starting up ...

After a while the following appears:
ALERT! /dev/sda2 does not exist. Dropping to a shell!

Busybox v1.1.3 ..... etc

I have tried to create a sepereate small boot partition.
I have tried installing on the other disk(There are 2Gb & 9Gb disks)

I also managed after quite a lot of pain to get the UUID for the first partition and have tried to use that in GRUB
root=dev/sda2 sda1 sdb1 sdb2 
root=UUID=...
That however gives me the exact same error.

The scsi controller have a very cool row of red LED's and when Grub is showing Starting Up they just go left and right the whole time as if searching for something. Looks like Night Rider...

I'm not sure what I should try next and any suggestions would be appreciated. If I need to provide more data just let me know.

---

